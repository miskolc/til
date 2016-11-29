mix phoenix.serve
** (CaseClauseError) no case clause matching: {:error, :tokens}
    (kernel) file.erl:1368: :file.consult_stream/3
    (kernel) file.erl:978: :file.consult/1
    (mix) lib/mix/compilers/elixir.ex:350: Mix.Compilers.Elixir.parse_manifest/2
    (mix) lib/mix/compilers/elixir.ex:37: Mix.Compilers.Elixir.compile/5
    (mix) lib/mix/task.ex:296: Mix.Task.run_task/3
    (elixir) lib/enum.ex:1184: Enum."-map/2-lists^map/1-0-"/2
    (elixir) lib/enum.ex:1184: Enum."-map/2-lists^map/1-0-"/2
    (mix) lib/mix/tasks/compile.all.ex:19: anonymous fn/1 in Mix.Tasks.Compile.All.run/1
    (mix) lib/mix/tasks/compile.all.ex:37: Mix.Tasks.Compile.All.with_logger_app/1
    (mix) lib/mix/task.ex:296: Mix.Task.run_task/3
    (mix) lib/mix/tasks/compile.ex:84: Mix.Tasks.Compile.run/1
    (mix) lib/mix/task.ex:296: Mix.Task.run_task/3
    (mix) lib/mix/task.ex:319: Mix.Task.get_task_or_run/3
    (mix) lib/mix/task.ex:279: Mix.Task.run_task/3
    (mix) lib/mix/cli.ex:58: Mix.CLI.run_task/2
    (elixir) lib/code.ex:363: Code.require_file/2
    
    
    Fix rm -rf _build && mix do clean, compile 
    de la https://github.com/parroty/exvcr/issues/24#issuecomment-122477302
    
