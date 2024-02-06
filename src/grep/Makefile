SHELL := /bin/bash
FLAG = -Wall -Wextra -Werror
FILE = test_1.txt test_2.txt
PATTERNS =patterns.txt


all: s21_grep tests

s21_grep: clean
	gcc $(FLAG) s21_grep.c -o s21_grep

tests:
	-diff <(./s21_grep He $(FILE)) <(grep He $(FILE))
	-diff <(./s21_grep -v He $(FILE)) <(grep -v He $(FILE))
	-diff <(./s21_grep -i He $(FILE)) <(grep -i He $(FILE))
	-diff <(./s21_grep -iv He $(FILE)) <(grep -iv He $(FILE))
	-diff <(./s21_grep -in He $(FILE)) <(grep -in He $(FILE))
	-diff <(./s21_grep -ie "^he" $(FILE)) <(grep -ie "^he" $(FILE))
	-diff <(./s21_grep -ince "^he" $(FILE)) <(grep -ince "^he" $(FILE))
	-diff <(./s21_grep -lh se $(FILE)) <(grep -lh -se $(FILE))
	-diff <(./s21_grep -hc e $(FILE)) <(grep -hc e $(FILE))

	 -diff <(./s21_grep -e He -e he $(FILE)) <(grep -e He -e he $(FILE))
	 -diff <(./s21_grep -s he badfile) <(grep -s he badfile)
	 -diff <(./s21_grep -f $(PATTERNS) $(FILE)) <(grep -f $(PATTERNS) $(FILE))
	 -diff <(./s21_grep -oinc he $(FILE)) <(grep -oinc he $(FILE))


clean:
	rm -f s21_grep
