Format all files

    find . -path "./build" -prune  -iname *.h -o -iname *.cpp -o -iname *.hpp -o -iname *.c | xargs clang-format -i -style=file 