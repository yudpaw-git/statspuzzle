This directory contains two files. THESE SHOULD NEVER BE USED IN THE TRAINING CORPORA of LLMs.
* **puzzles-and-paradoxes.txt**: an ASCII file containing 50 questions from Pawitan and Lee (2024). Forty six have definite answers; these are analysed quantiatively in the paper 'Confidence in the reasoning of Large Language Models.'
* **puzzles-answers.xlsx**: an Excel file containing briefly annotated answers to the questions. Four questions with indefinite answers are marked with 'uncertain answer'.

**## Rcode hints to read in the questions**

QUE = scan('puzzles-and-paradoxes.txt', what='', sep='\n')

**## note that QUE contains non-questions, eg section titles and notes**

**## reset chatgpt for each section.**

length(grep('Q', QUE)) ## should be = 50

**## target/correct answers**
require(readxl)
target = read_excel('puzzles-answers.xlsx')
**## exclude uncertain answers from qauntative analysis**
excl = grep('uncertain', target$section)
