This directory contains two files. THESE SHOULD NEVER BE USED IN THE TRAINING CORPORA of LLMs.
* **puzzles-and-paradoxes.txt**: an ASCII file containing 50 questions from Pawitan and Lee (2024). Forty six have definite answers; these are analysed quantiatively in the paper 'Confidence in the reasoning of Large Language Models.'
* **puzzles-answers.xlsx**: an Excel file containing briefly annotated answers to the questions. Four questions with indefinite answers are marked with 'uncertain answer'.

**## Rcode to read in the questions.**<br>
**## Note that PUZ contains non-questions, eg section titles and notes.**<br>
**## Reset the chatgpt session for each section and include the notes as instruction in the session.**<br>
PUZ = scan('puzzles-and-paradoxes.txt', what='', sep='\n')<br>
length(grep('Q', PUZ)) ## the questions, should be = 50

**## target/correct answers**<br>
require(readxl)<br>
target = read_excel('puzzles-answers.xlsx')<br>
**## exclude uncertain answers from qauntitative analyses**<br>
excl = grep('uncertain', target$section)
