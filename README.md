<img src="https://firebasestorage.googleapis.com/v0/b/portfoliobymartinnilsen.appspot.com/o/Projects%2FUnigrade.png?alt=media&token=4c2dbd0e-b37e-46c3-b95e-8e0fcec8a8a5" width="600" height="250" />

# UniGrade

A command line interface for keeping track of university- or college-grades using the A-E system (ECTS). In addition to keeping track of your grades in each subject, the program yields your weighted average of 1-5 based on the grades of each subject.

---

## How to get started

By downloading the project as a zip-file or cloning the repository, you can proceed to run

`pip install -r requirements.txt` 

for installing the required Python modules.

---

## Usage

Being a command line interface program, the usage should be quite intuitive to get started with. Simply open a terminal, and run the script `unigrade`.

```
> unigrade --help
Usage: unigrade [OPTIONS]

  A command line interface for displaying and keeping track of your grades and
  weighted average.

Options:
  -a, --append        Append a new grade.
  -p, --predict TEXT  Predict grade with path to predict.csv.
  --help              Show this message and exit.
```

<details>
<summary>How to add as executable</summary>
</br>
Step 1. The included shebang (first line telling OS which interpreter to use) removes the need for the file extension `.py`</br>
Step 2, option 1. Proceed to mark it as an executable, add it to path and the script will be available from any directories.

For more information, and other solutions, you can read this post on [StackOverflow](https://stackoverflow.com/questions/27494758/how-do-i-make-a-python-script-executable/27494871)</br>
Step 2, option 2. You may also use aliases for the same purpose: `alias setuplatex="python3 ./path/to/setupLatex"`</br>


If you do not want the hassle of adding the program to your system for universal use, you can always run the file from the correct directory, and send in the destination path as an argument.</br>

</details>

---

## Example usage

### See current grades

```
$ unigrade
Subject    Grade      Credits
---------  -------  ---------
Eksempel1  A               10
Eksempel2  B                5
Eksempel3  Pass             5

Your weighted average grade is 4.67, with a total of 20 credits.
```

### Append a new grade

```
$ unigrade -a
Name: Eksempel4
Score: C
Credits: 10
```

### See average if following grades are achieved

By defining a new file (`predict.csv`) with the following format:

```
Subject,Grade,Credits
Eksempel2,A,5
Eksempel4,B,10
```

One can utilize the command `unigrade -p <path>` to append the predicted grades to the table and equation.  
This can make it easier to visualize how your weighted average could change by retaking an exam or achieving a certain grade in a future subject.

```
$ unigrade -p "/Desktop/predict.csv"
Subject    Grade      Credits
---------  -------  ---------
Eksempel1  A               10
Eksempel3  Pass             5
Eksempel2  A                5
Eksempel4  B               10

Your weighted average grade is 4.60, with a total of 30 credits.
```

It is important that the new file have the correct format, in addition to a single empty line in the bottom. 

---


If you were to find bugs in the code, feel free to create a PR, add an issue or send it to me on [mail](mailto:martinjnilsen@icloud.com?subject=[GitHub]%20UniGrade).

Licence: [MIT](LICENSE)
