

PART A — PROJECT SETUP USING THE CLI

cd ~
mkdir python_lab
cd python_lab
mkdir src tests docs
touch src/main.py src/utils.py src/config.py
echo "My Python Lab Project" > docs/README.md
find .

Expected structure:

python_lab/
├── src/
│   ├── main.py
│   ├── utils.py
│   └── config.py
├── tests/
└── docs/
    └── README.md

Explanation:
"cd" changes the directory, "mkdir" creates directories, "touch" creates empty files, "echo" writes text to a file, and "find ." displays the directory structure recursively.

Separating "src", "tests", and "docs" keeps source code, testing files, and documentation organized. This makes the project easier to maintain and expand.

---

PART B — GIT INITIALIZATION AND FIRST COMMIT

git init

cat > .gitignore <<EOF
__pycache__/
*.pyc
.env
EOF

git add .
git status
git commit -m "Set up Python lab project structure"
git log --oneline

Explanation:
".gitignore" tells Git which files should not be tracked. "__pycache__/" and "*.pyc" ignore Python-generated cache and compiled files, while ".env" prevents environment configuration files from being committed.

The commit history shows the changes made to the project over time, including commit messages and commit IDs.

---

PART C — WRITING AND COMMITTING PYTHON CODE

"src/utils.py"

def square(n):
    return n ** 2


def is_even(n):
    return n % 2 == 0


def celsius_to_fahrenheit(c):
    return (c * 9 / 5) + 32

"src/main.py"

from utils import square, is_even, celsius_to_fahrenheit


number = float(input("Enter a number: "))

print("Square:", square(number))

if is_even(number):
    print("The number is even.")
else:
    print("The number is odd.")

print("Fahrenheit:", celsius_to_fahrenheit(number))

Run the Program

python3 src/main.py

Test 1

Enter a number: 3
Square: 9.0
The number is odd.
Fahrenheit: 37.4

Test 2

Enter a number: 10
Square: 100.0
The number is even.
Fahrenheit: 50.0

Test 3

Enter a number: 25
Square: 625.0
The number is odd.
Fahrenheit: 77.0

Commit the Changes

git add src/main.py src/utils.py
git commit -m "Add utility functions and main program"

Explanation:
"main.py" imports the functions from "utils.py" using the "from utils import ..." statement. This allows the main program to use reusable functions defined in the separate "utils.py" file.

---

PART D — GITHUB AND BRANCH WORKFLOW

1. Create the GitHub Repository

Create a public GitHub repository named:

python-lab

Do not initialize it with a README.

2. Connect and Push the Local Repository

cd ~/python_lab
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/python-lab.git
git push -u origin main

Replace "YOUR-USERNAME" with your GitHub username.

3. Create the Feature Branch

git checkout -b feature/add-greeting

4. Add "greet()" to "src/utils.py"

def greet(name):
    return f"Hello, {name}! Welcome to the Python Lab."

Complete "utils.py":

def square(n):
    return n ** 2


def is_even(n):
    return n % 2 == 0


def celsius_to_fahrenheit(c):
    return (c * 9 / 5) + 32


def greet(name):
    return f"Hello, {name}! Welcome to the Python Lab."

5. Update "src/main.py"

from utils import square, is_even, celsius_to_fahrenheit, greet


name = input("Enter your name: ")
print(greet(name))

number = float(input("Enter a number: "))

print("Square:", square(number))

if is_even(number):
    print("The number is even.")
else:
    print("The number is odd.")

print("Fahrenheit:", celsius_to_fahrenheit(number))

6. Test, Commit, and Push

python3 src/main.py

git add src/main.py src/utils.py
git commit -m "Add personalized greeting feature"
git push -u origin feature/add-greeting

7. Create the Pull Request

On GitHub, create a pull request:

feature/add-greeting → main

Pull Request Title:

Add personalized greeting feature

Required Screenshots

- Part A: Recursive directory listing.
- Part B: First commit history.
- Part D: GitHub repository showing files and commits.
- Part D: Open pull request from "feature/add-greeting" to "main".
