# The missing vimspector python docker documentation

Since I spent more time than I would care to admit in getting a trivial python-in-docker example
working with vimspector, here are my findings:

Have a look at [.vimspector.json](/.vimspector.json); the attach-run configuration first runs
the included [run_with_debugpy](/run_with_debugpy) shell script, which runs the given script with debugpy inside
of a newly created docker container.

Opening any python file in this repo and issuing `:vimspector#Launch()` should just work.
However, I have found that adding `stopAtEntry: true` does nothing, and hence you need to first
add a breakpoint; otherwise, I guess by the time vimspector connects and issues that first stop
command, the debugpy process is already finished executing the script.
