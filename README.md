# MasterMind
	import random                                         
	import time  
	from tkinter import *

	def select_level():
    	global level
    	level = level_selector.get()
    	root.destroy()

	root = Tk()
	level_selector = Scale(root, from_=1, to=3, tickinterval=1)
	level_selector.set(0)
	level_selector.pack()
	Button(root, text="Select a difficulty level", command=select_level).pack()

	mainloop()

	cpc_1_digit = 0
	cpc_2_digit = 0
	cpc_3_digit = 0
	cpc_4_digit = 0
	p_1_digit = 0
	p_2_digit = 0
	p_3_digit = 0
	p_4_digit = 0
	correct_correct = 0
	correct_wrong = 0
	chances = 0

	if level == 1:
    	chances = 15
	elif level == 2:
    	chances = 10
	else:
    	chances = 7

	cpc_1_digit = random.randint(0, 9)

	while cpc_2_digit == cpc_1_digit or cpc_2_digit == cpc_3_digit or cpc_2_digit == cpc_4_digit:
    	cpc_2_digit = random.randint(0, 9)

	while cpc_3_digit == cpc_1_digit or cpc_3_digit == cpc_2_digit or cpc_3_digit == cpc_4_digit:
    	cpc_3_digit = random.randint(0, 9)

	while cpc_4_digit == cpc_1_digit or cpc_4_digit == cpc_2_digit or cpc_4_digit == cpc_3_digit:
    	cpc_4_digit = random.randint(0, 9)

	while chances > 0:
    	correct_correct = 0
    	correct_wrong = 0

			answer = input("Enter a four-digit number with different digits (e.g 1476): ")
    	p_1_digit = int(answer[0])
    	p_2_digit = int(answer[1])
    	p_3_digit = int(answer[2])
    	p_4_digit = int(answer[3])

    	if p_1_digit == cpc_1_digit:
        	correct_correct = int(correct_correct) + 1
    	elif p_1_digit == cpc_2_digit or p_1_digit == cpc_3_digit or p_1_digit == cpc_4_digit:
        	correct_wrong = int(correct_wrong) + 1
    	else:
        	pass

    	if p_2_digit == cpc_2_digit:
        	correct_correct = correct_correct + 1
    	elif p_2_digit == cpc_1_digit or p_2_digit == cpc_3_digit or p_2_digit == cpc_4_digit:
        	correct_wrong = int(correct_wrong) + 1
    	else:
        	pass

    	if p_3_digit == cpc_3_digit:
        	correct_correct = int(correct_correct) + 1
    	elif p_3_digit == cpc_1_digit or p_3_digit == cpc_2_digit or p_3_digit == cpc_4_digit:
        	correct_wrong = int(correct_wrong) + 1
    	else:
        	pass

    	if p_4_digit == cpc_4_digit:
        	correct_correct = int(correct_correct) + 1
    	elif p_4_digit == cpc_1_digit or p_4_digit == cpc_3_digit or p_4_digit == cpc_2_digit:
        	correct_wrong = int(correct_wrong) + 1
    	else:
        	pass

    	print("")
    	if int(correct_correct) == 4:
        	print("Congratsulations! You found the computer's number!")
        	break
   	  elif int(correct_wrong) > 0 or int(correct_correct) >= 1 and int(correct_correct) < 4:
        	print("You got " + str(correct_correct) + " correct digit(s) in the correct place, and " + str(correct_wrong) + " correct 	digit(s) but in wrong place.")
    	elif int(correct_correct) == 0 and int(correct_wrong) == 0:
        	print("You didn't guess any number, try again!")
    	else:
        	raise Exception("CheckError: line 69, something went wrong with the comparisons.")
        	exit()
    	print("")

    	chances = chances - 1
    
	if chances == 0:
    	print("You lost... The secret number was " + str(cpc_1_digit) + str(cpc_2_digit) + str(cpc_3_digit) + str(cpc_4_digit) + ". Try 	again by rerunning the program.")

	time.sleep(4)
