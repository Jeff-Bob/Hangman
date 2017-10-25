# Hangman
import tkinter

def logout():
    logoutwindow = tkinter.Tk()
    logoutwindow.title("logout")
    lblInst = tkinter.Label(logoutwindow, text="please confirm:")
    lblInst.pack()
    canclebtn = tkinter.Button(logoutwindow, text="cancel", command = options)
    canclebtn.pack()
    conbtn = tkinter.Button(logoutwindow, text="confirm", command = quit)
    conbtn.pack()
    logoutwindow.mainloop()

def hangman():
    
    wrong1 = ("_______")

    wrong2 = ('''
                |
                |
                |
                |
                |_______''')

    wrong3 = ('''
                _____
                |
                |
                |
                |
                |_______''')

    wrong4 = ('''
                _____
                |
                |
                |
                |_
                |_|______''')

    wrong5 = ('''
                _____
                |   | 
                |
                |
                |_
                |_|______''')

    wrong6 = ('''
                _____
                |   | 
                |   o
                |
                |_
                |_|______''')

    wrong7 = ('''
                _____
                |   | 
                |   o
                |   |
                |_  
                |_|______''')

    wrong8 = ('''
                _____
                |   | 
                |   o
                |  /|\
                |_  
                |_|______''')

    wrong9 = ('''
                _____
                |   | 
                |   o   
                |  /|\
                |_ / 
                |_|______''')

    dead = ('''
                _____
                |   | 
                |   o   
                |  /|\
                |_ / \
                |_|______''')

    word = (input("enter word to be guessed"))
    guesses = ''
    turns = 10
    while turns > 0:         
        failed = 0                
        for c in word:      
            if c in guesses:    
                print (c)
            else:
                print ("_")     
                failed += 1    
        if failed == 0:        
            print ("You won")  
            break              

        guess = (input("guess a character:")) 
        guesses += guess                    
        if guess not in word:  
            turns -= 1        
            print ("Wrong")
            if turns == 9:
                print (wrong1)
            elif turns == 8:
                print (wrong2)
            elif turns == 7:
                print (wrong3)
            elif turns == 6:
                print (wrong4)
            elif turns == 5:
                print (wrong5)
            elif turns == 4:
                print (wrong6)
            elif turns == 3:
                print (wrong7)
            elif turns == 2:
                print (wrong8)                      
            elif turns == 1:
                print (wrong9)
            else:
                print (dead)
            print ("You have", + turns, 'more guesses') 
            if turns == 0:
                print ("You Loose")
                quit()          
    
def options(loginwindow):
    loginwindow.destroy()
    optionwindow = tkinter.Tk()
    optionwindow.title("options")
    optionwindow.geometry ("200x100")
    lblInst = tkinter.Label(optionwindow, text="choose an option:")
    lblInst.pack()
    btn2 = tkinter.Button(optionwindow, text="play", command = hangman)
    btn2.pack()
    btn3 = tkinter.Button(optionwindow, text="logout", command = logout)
    btn3.pack()
    optionwindow.mainloop()

def login():
    username = entUsername.get()
    password = entPassword.get()
    if username == "c" and password == "p":
        print ("Welcome")
        options(loginwindow)
    else:
        print ("not quite")    
    

loginwindow = tkinter.Tk()
loginwindow.title("Welcome")
lblInst = tkinter.Label(loginwindow, text="please login to continue:")
lblInst.pack()
lblUsername = tkinter.Label(loginwindow, text="Username:")
entUsername = tkinter.Entry(loginwindow) 
lblUsername.pack()
entUsername.pack()
lblPassword = tkinter.Label(loginwindow, text="Password:")
entPassword = tkinter.Entry(loginwindow)
lblPassword.pack()
entPassword.pack()
btn = tkinter.Button(loginwindow, text="login", command= login)
btn.pack()
loginwindow.mainloop()
