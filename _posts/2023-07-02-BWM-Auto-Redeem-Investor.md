---
title: "BINANCE WEALTH MATRIX AUTOMATED REDEEM / INVESTOR"
date: 2023-07-03T16:00:00-00:00
categories: [BWM, Automation]
tags: [Binance, Wealth, Matrix, Automated, Redeem, Investor]
img_path: /images/
image:
  path: console.png
  alt: Console Screenshot
---

## What is it?

The Binance Wealth Matrix Automated Redeem / Investor is an application that allows you to automate your Binance Wealth Matrix Redeem / Invest cycles.  By default, the application will automatically perform a Redeem action, determine the amount Redeemed (in BUSD or USDT) and then perform an Invest action for the same amount.  This ensures that you are always "reinvesting" 100% of your Redeemed CLIMB tokens value, whilst at the same time, increasing the price of CLIMB.  However, you can specify your own Redeem to Invest ratio, allowing you to implement your favorite strategies (i.e 1:1, 50/50, 75/25 etc).


## Features
- Available for Windows / Mac / Linux based Operating Systems.
- Makes direct Web3 calls in the background and does not rely on "screen clickers" / automation software that takes control of your device.
- Specify your Redeem to Invest ratio, allowing you to implement your favorite strategies (i.e 1:1, 50/50, 75/25 etc).
- Use in conjunction with task scheduling software (i.e Windows Task Scheduler or pm2 for Mac) to create as many bespoke invest / redeem schedules, (tailored to your strategies), as you like.
- Utilises the Ankr RPC endpoint in order to ensure the lowest gas fees.
- Makes use of an automatic stepped gasPrice increase / transaction resubmit mechanism, should a lower gasPrice value cause a transaction to timeout.  This ensures you are always paying the lowest gas fees you can, based on network congestion.
- Can be used on multiple devices.

## Requirements
- You need to have already made at least one Invest via the DApp at https://binancewealthmatrix.com/matrix, prior to using this application.
- You need to obtain your wallet private key.
- You need to have enough BNB in your wallet to cover the transaction gas fees.


## Installation and Configuration
1. Extract the contents of the zip file to a folder of your choice.
2. Right click on the .env file and open with a text editor of your choice (i.e Notepad) and you will see three fields :-
```plaintext
WALLET_ADDRESS=""
PRIVATE_KEY=""
INVEST_RATIO="1"
```
3. Enter your Binance Smart Chain BEP-20 wallet address in the WALLET_ADDRESS field (between the quotation marks).
4. Enter your Binance Smart Chain BEP-20 wallet private key in the PRIVATE_KEY field (between the quotation marks).
5. (Optional) Amend the Redeem to Invest ratio in the INVEST_RATIO field (between the quotation marks).  This value represents the ratio of your Redeem to Invest cycles.  By default, this value is set to "1", which will Invest 100% of your Redeemed CLIMB back into the Binance Wealth Matrix.  You can amend this value to suit your investement strategies.  For example, if the value of your Redeemed CLIMB is 100 BUSD, here is how much will be Invested back into the Binance Wealth Matrix, based on the INVEST_RATIO value :-
```plaintext
INVEST_RATIO="1" - Invest 100 BUSD
INVEST_RATIO="0.5" - Invest 50 BUSD
INVEST_RATIO="0.25" - Invest 25 BUSD
INVEST_RATIO="0.75" - Invest 75 BUSD
INVEST_RATIO="2.0" - Invest 200 BUSD
INVEST_RATIO="0" - Invest 0 BUSD (i.e 100% Redeem, 0% Invest)
```
6. Save the .env file.


## One Time Usage
The application should ideally be used in conjunction with Windows Task Scheduler (Windows) or PM2 (Mac OSX / Linux) to create as many bespoke invest / redeem schedules, (tailored to your strategies), as you like.  However, if you just want to run the application once, you can do so by following the steps below :-

- Double click on the BWM_Automated_Redeem_Investor.exe file to start the application.
- A console window will appear on screen, validation checks will then take place on the data entered into the .env file. If successful, the application will start.  If validation fails, you will be prompted to check the data entered into the .env file.
- The application will perform one Invest and Redeem cycle (assuming the INVEST_RATIO value is not set to "0") and then exit.
- The application will first attempt a transaction, using a very low gasPrice value (1 GWEI), on the Ankr RPC endpoint.  If the transaction times out, the application will automatically increase the gasPrice value and resubmit the transaction.  This process will continue until the transaction is successful.
- The output of the script will be displayed in the console window and also written to a log file (climb.log) in the same folder as the executable file.  This will contain details such as the transaction hash, gas fees paid, gasPrice used, Redeemed CLIMB amount, Invested CLIMB amount and the Redeem to Invest ratio used, for each transaction.  To open the climb.log file, double click on it and it will open in your default text editor.


## Scheduled Usage
The application should ideally be used in conjunction with Windows Task Scheduler (Windows) or PM2 (Mac OSX / Linux) to create as many bespoke invest / redeem schedules, (tailored to your strategies), as you like.  This will allow you to automate your Binance Wealth Matrix Redeem / Invest cycles, without having to manually run the application each time.  To do this, follow the steps below :-

### Windows Task Scheduler
1. Open Windows Task Scheduler.
2. Click on "Create Task" in the right hand pane.
3. Enter a name for the task (i.e BWM Automated Redeem / Invest).
4. Click on the "Triggers" tab and then click on "New".
5. Configure the schedule as required and then click on "OK".
7. Click on the "Actions" tab and then click on "New".
8. Click on "Browse" and navigate to the folder where you extracted the application files to.
9. Select the BWM_Automated_Redeem_Investor.exe file and then click on "Open".
10. Click on "OK".

The application will then run automatically at the schedule that you configured in step 5.

An alternative method to acheive this can be seen on the following YouTube video :- https://www.youtube.com/watch?v=DVUlkU2AxgQ.


### PM2 (Mac OSX / Linux)
A similar process can be followed for Mac OSX / Linux based Operating Systems, using PM2 with the cron time scheduling option.  For more information on how to do this, please see the following link :- https://pm2.keymetrics.io/docs/usage/quick-start/.

This is the process that I personally use, so I can help you set this up if you need assistance.

## Using multiple .env files for different schedules / wallet addresses
If you want to create multiple schedules on the same or different wallet addresses, with different INVEST_RATIO values set :-

1. Create multiple copies of the folder you extracted in step 1 of the "Installation and Configuration" section above.  
2. Edit the .env file for each schedule / wallet address, configuring the INVEST_RATIO value accordingly.
3. Create a separate schedule for each folder, using the steps outlined in the "Scheduled Usage" section above.

## Disclaimer

This application has been thoroughly tested and is working as expected.  However, as with any software, there is always the possibility of bugs.  Please use this application at your own risk.

You are entirely responsible for your wallet private key and the security of your wallet.  The author of this application accepts no responsibility for any loss of funds, should your private key be compromised in any way.

## Support

If you need any assistance with this application, please contact me on Telegram @ [https://t.me/MadgeMcMahon]









































