# ATM-Project-Python


## Overview
This Python project simulates an ATM (Automated Teller Machine) system. It provides options for Banking operations such as balance inquiry, withdrawal,deposit and Return card.
<br>

## ATM Simulator Program Pseudo Code:

This is a pseudo code representation of an ATM simulator program for ABC Bank.

### Initialization
- Set initial account balance `curr_bal`.
- Define account number `accno`.
- Set minimum balance `min_bal` to £300.
- Define default password `passwd`.
- Initialize exception count `excpt_cnt` to 0.

### User Authentication
- Iterate 3 times for password entry:
  - Prompt user to enter password.
  - If entered password matches `passwd`, exit loop.
  - If password entry fails after 3 attempts, inform user and terminate.
  <br>
  
![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/157f71ec-8442-424c-8ac6-c8cb86cca6a3)

<br>

### Main Program Loop
- Display welcome message and menu options:
  - Display Balance
  - Withdraw Funds
  - Deposit Funds
  - Return card
- Prompt user to select an option.
<br>

![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/276a4c13-0472-48dc-8152-bc8d2a33d555)

<br>
<br>

### Display Balance
- Display current account balance `curr_bal`.
<br>

![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/b737cfe7-6a23-466d-b58e-d78b06be007b)
<br>
<br>

### Withdraw Funds
- Prompt user to select withdrawal amount:
  - £10
  - £20
  - £40
  - £60
  - £80
  - £100
  - Other amount
  - Return to main menu
- Adjust account balance based on selected withdrawal option.
<br>

![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/ec7ea55b-5a84-445f-a8a5-65ca11b60df6)

<br>
<br>

### Deposit Funds
- Prompt user to enter deposit amount.
- Check if deposit amount is within limits (minimum and maximum).
- Update account balance with the deposited amount.
<br>

![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/2ba09ad9-a40d-4f14-bfc6-6a5c76f13b6b)
<br>
<br>

### Error Handling
- Handle exceptions for invalid user inputs.
- Inform the user about any errors and prompt for correct inputs.
<br>

![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/7ae571d2-71b1-4e28-878a-a3b65d625d0f)

<br>
<br>

## Return card:


![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/4ff8f93c-606c-4fcd-b9d4-16421cc5007b)
<br>
<br>


### Conclusion
This pseudo code outlines the functionality of an ATM simulator program, including user authentication, balance checking, fund withdrawal, fund deposit, and error handling.

<br>
<br>

## ATM Program Code:
<br>

```python
#ATM Program ABC Bank
curr_bal = 2000.56
accno = 1020506
min_bal = 300
a =1
b =1
c = 1
d= 1
excpt_cnt =0
passwd = 'OpenAcct!'
for i in range(3):
     pswd1 = input("\nPlease Enter your pasword: ")
     if passwd == pswd1:
         break
     elif passwd != pswd1:
          if i==2:
             print("\nTry again later")
          continue
if passwd == pswd1:
   while c > 0:
       print("\nWelcome to ABC Bank", "1 - Display Balance","2 - Withdraw Funds","3 - Deposit Funds","9 - Return card", sep = '\n')
       b = 1
       try:
           menu = int(input("\nPlease enter an option: "))
           if menu == 9:
               print("\nThank you for Banking with us, Please Collect your Card")
               c = 0
               break
           elif menu == 1:
               print(f'\nYour Account {accno} balance is £{curr_bal}')
               break
           elif menu ==2:
                  #b = 1
                  while b > 0:
                      print("\nPlease select withdrawal amount","1 - £10","2 - £20","3 - £40","4 - £60","5 - £80","6 - £100","7 - other amount","8 - Return to main menu", sep ='\n')
                      try:
                             n = int(input("\nEnter the withdrawal option "))
                             if 1<=n<=6:
                                 option1 = [10,20,40,60,80,100]
                                 curr_bal = curr_bal - option1[n-1]
                                 print(f'\n£{option1[n-1]} has been withdrawn from your account {accno}. Your current balance is £{curr_bal}')
                                 b= 0
                                 break
                             #continue
                             elif n == 7:
                                 a = 1
                                 if (curr_bal <= min_bal):
                                              print(f'\nYour account balance is £{curr_bal}, the minimum account balance should be £{min_bal}. Balance amount in your account is insuffiecient')
                                              b = 0
                                              break
                                 a = 1#continue
                                 while a > 0:
                                    withdr = int(input("\nEnter the withdrawal amount "))
                                    if (withdr%10 !=0):
                                       print("\nPlease Enter the amount in multiples of 10")
                                       break
                                    elif(withdr%10==0):
                                        check_bal = curr_bal- min_bal
                                        wdrl_limit = 200
                                        if withdr > wdrl_limit:
                                                print(f'\nPer day Withdrawal amount is £{wdrl_limit}. So Please enter an withdrawal amount within the limit.')
                                                break
                                        else:
                                                    curr_bal = curr_bal - withdr
                                                    print(f'\n£{withdr} has been withdrawn from your account, Your current balance is  £{curr_bal}')
                                                    a = 0
                                                    b = 0
                                                    break
                                        break
                                    continue
                                 #break
                             elif n==8:
                                b = 0
                                break
                             continue   # for try menu 2
                      except ValueError:
                           print("\nPlease enter an option from 1 to 8\n")
                      #finally:
                      #     continue
                  break
           elif menu == 3:
                d = 1
                while d>0:
                    try:
                         dep = int(input("\nPlease enter the deposit amount "))
                         if dep < 50:
                              print("\nMinimum deposit amount is £50, Please enter amount greater than £50")
                              continue

                         elif dep>300:
                              print("\nMaximum deposit limits per day is £300. Please deposit within the limit")
                              continue
                         else:
                              curr_bal+= dep
                              print(f'\nAmount Deposited Successfully, Your account {accno} has a total balance of £{curr_bal}')
                              d = 0
                              break
                         continue # continue for try
                    except ValueError:
                              print("\nPlease enter an amount in numbers")
                    except TypeError:
                              print("\nPlease Enter the amounts in whole numbers")
                    continue
                break
           continue # for try main menu
       except ValueError:
              excpt_cnt+=1
              if excpt_cnt==2:
                 print("\nThank you for Banking with us, Please collect your Card.")
                 c=0
              else:
                print("\nPlease enter a valid option")
       finally:

               continue
```
<br>
  
![image](https://github.com/SubashiniMahadevan/ATM-Project-Python/assets/168095179/9448f169-e50f-4cc4-a2fd-c7eeb684b0eb)
<br>


 







