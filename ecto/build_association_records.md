## Inserting Records with `build_assoc/3`

#### build_assoc(struct, assoc, attributes \\ %{})[1]

You don't need to add the `id` of the record that `has` the record you want to build, it's done automatically by the build function.

For example, if you want to build a record that it's `owned` by a `category` record, it's `category_id` foreign key will be automatically set to `category.id` by the `build_assoc/3` function

      defp _insert_via_association(category) do
        changeset = category
          |> build_assoc(:leaf_category_list, %{list: (category.id |> Integer.to_string)})
        Repo.insert!(changeset)
      end


You also don't need to allow the foreign key in the cast method of the changeset

      def changeset(struct, params \\ %{}) do
        struct
        |> cast(params, [:list])  # <==== Don't need :category_id here
        |> validate_required([:list])
        |> foreign_key_constraint(:category_id)
      end

## Context [2]
 
## Alternatives
 
#### Insert using Changeset by allowing foreign key fields explicitely [3]
 
[1]: https://hexdocs.pm/ecto/Ecto.html#build_assoc/3
[2]: https://github.com/miskolc/til/blob/master/ecto/changeset_cast.md#context
[3]: https://github.com/miskolc/til/blob/master/ecto/changeset_cast.md#allow-fields-explicitly
 
