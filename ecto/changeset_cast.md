## Allow fields explicitly

#### cast(data, params, allowed)[1]

You have to allow the fields you want to change explicitly in the `cast/3` method's third parameter( `allowed`):

        iex(27)> changeset = %{category_id: 1}                                   
        %{category_id: 1}
        iex(28)> changeset = cast(%LeafCategoryList{}, changeset, [])            
        #Ecto.Changeset<action: nil, changes: %{}, errors: [],
         data: #BlackFriday.LeafCategoryList<>, valid?: true>
        iex(29)> changeset = %{category_id: 1}                                   
        %{category_id: 1}
        iex(30)> changeset = cast(%LeafCategoryList{}, changeset, [:category_id])
        #Ecto.Changeset<action: nil, changes: %{category_id: 1}, errors: [],
         data: #BlackFriday.LeafCategoryList<>, valid?: true>
    
Had to put the `category_id` inside the allowed list:
         
          def changeset(struct, params \\ %{}) do
            struct
            |> cast(params, [:list, :category_id])
            |> validate_required([:list])
            |> foreign_key_constraint(:category_id)
          end
         
## Context

#### Had problems when inserting the leaf category lists for each category in the database
The values for the foreign key column where not added to the table because Phoenix doesn't seem to add the foreign key column to the `allowed` list

`In general - use changeset function for data from external sources. When you do stuff programatically you can create the struct in place` - [2]


`If you want to build the struct programatically, you can like with any other struct - i.e. `%Foo{bar: baz}`
Use `cast/3` for dealing with external data that needs conversion
If you're already in a changeset, you can use `change/2` for programatic modifications`


[1]: https://hexdocs.pm/ecto/Ecto.Changeset.html#cast/3
[2]: https://github.com/michalmuskala
