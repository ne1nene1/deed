# deed
managing your todo in todo.txt format

## installation
make file executable
```shell
chmod +x ./deed
```
add to your path
```shell
mv deed /path/to/your/bin
```
or add alias to your shell config
```shell
alias deed="/path/to/this/script"
```
## overview
by default, deed will operate on TODO_FILE for (almost) all operation. you can
change the target file by specified `-t,--target` flag to operate on different file
inside TODO_DIR directory
```shell
deed -t backlog -a TASK                # add TASK to backlog file
deed -t someday -del INDEX             # delete task at index INDEX in someday file
deed -t someday -mov INDEX todo        # move task at index INDEX from someday to todo file
```
index specification could be a single digital, an array of digit or a sequence of digital
for example:
    if you specified index 9, the action will operate on task at index 9
    if you specified index 1,2,3 the action will operate on task at index 1,2 and 3. 
    if you specified index 1,4..6 the action will operate on task at index 1,4,5 and 6
```shell
deed -app "@home" 1,4,6                # append "@home" to tasks at index 1,4,6
deed -del 3..5,7                       # delete tasks at index 3,4,5,7
```
the now option is a little different. it just a filter option but it is used for filter
common pattern in your todo file. for example, if you work on a project in which 
you append all of the todos with +project tag, but you also want it to only show todos that also have
@home tag. by customizing now variable inside the script, you can quickly skip the hassle 
of typing `deed -f "(\+project|@home)"` everytime you want to query for todos on that project,
you could preconfigure the now variable to `(\+project|@home)` so that you can shorten the command to
just `deed -n` or `deed --now`
## usage
list tasks in files exist inside TODO_DIR
```shell
deed                                   # list task(s) in TODO_FILE
deed -l                                # list task(s) in both TODO_FILE and DONE_FILE
deed -l someday                        # list only task(s) from SOMEDAY_FILE
deed -l FILE                           # list only task(s) from FILE
```
add TASK to TODO_FILE
```shell
deed -a TASK
deed TASK                              # -a,--add can be omitted
```
mark TASK at index INDEX as done
```shell
deed -d INDEX
```
mark TASK at index INDEX with priority of PRIOR
```shell
deed -p INDEX PRIOR
deed -p 1 A
deed -p 1 a                            # PRIOR could be either lower or upper case
```
append TEXT to task at index INDEX
```shell
deed -app TEXT INDEX
```
delete task at index INDEX
```shell
deed -del INDEX
```
archive and move completed task inside TODO_FILE to DONE_FILE
```shell
deed -c                                # c for clean
```
open file
```shell
deed -o
```
log a total number of complete and incomplete task from TODO_FILE and DONE_FILE to REPORT_FILE
```shell
deed -r
```
move task at index INDEX from default target file to DESTI_FILE
```shell
deed -mov INDEX DESTI_FILE
```
only print task(s) that match regex REGEX
```shell
deed -f REGEX
```
change default target file for operation to TARGET_FILE
(TARGET_FILE must exists inside TODO_DIR)
```shell
deed -t TARGET_FILE
```
enable verbose logging mode
```shell
deed -v
```
print help message
```shell
deed -h
```

## resources
- [todo.txt format specification](https://github.com/todotxt/todo.txt)
- [todo.txt website](http://todotxt.org/)
- [todo.txt cli](https://github.com/todotxt/todo.txt-cli)

## author 
@ne1nene (Soulmine) [github](https://github.com/ne1nene1/)
