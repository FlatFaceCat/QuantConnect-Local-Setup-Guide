# QuantConnect-Local-Setup-Guide
Guide on setting up Quant Connect locally \
PLEASE NOTE: \
This guide was created for personal use as a reminder on how to set up QuantConnect to run locally VS hosted on the cloud. \
If any steps do not work, or do not make sense, please reach out or comment so I can update for future use. \

Version 1 = 09/29/2023 = Initial release \
Version 2 = 09/29/2023 = Removed personal details \

-----------------

## Download and install the following files: 
- [VS code](https://code.visualstudio.com/download)
- [Python 3.8.10](https://www.python.org/downloads/release/python-3810/)
- [Anaconda3](https://www.anaconda.com/download)
- [Docker](https://www.docker.com/products/docker-desktop/)

Open each program and log in / register if required 
-----------------

## Set up Anaconda navigator

Open "Anaconda Navigator", click on "enviroments" and then "create":

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/c9826d33-b88c-4b1c-a48c-042c21cd5926)

Give the ENV a name, choose the python enviroment and select version "3.8.17"

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/4fc887d3-ee3a-4e79-bec9-4c5bed281cf5)

Click "Create", allow the ENV to fully load, and then you can close the Anaconda Navigator application

-----------------

## Interface Anaconda with VS code 

Open "Visual Studio Code" and click on "File -> Preferences -> Settings"

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/34b5509f-6636-4ac4-9675-5e4c4c48f6b4)

From there, under the section "Extensions -> Python" Change the default Interpreter Path to the ENV created above. 

-----------------

## PIP Install 

To install python packages to your ENV, open "Anaconda Prompt", and then change to the project ENV you created by typing: 
```
conda activate quantconnect
```
This will activate the ENV and make sure PIP installed to the correct enviroment. From there, standard PIP protocol can be applied: 
```
pip install scikit-learn
```
(Replace scikit-learn with the required package)

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/bbbc14ec-6c80-46ad-8242-50b67c8e14c6)

-----------------

## Pip install Lean 

The Lean CLI needs to be installed, and this is handled via PIP. As above, make sure "Anaconda Prompt" is open and pointed to the correct project. 
Then install the lean library: 
```
pip install lean
```
![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/8944529f-8ec0-4721-bb5c-f1c67607a06f)

-----------------

## Lean create new project 

Use the "Anaconda Prompt" and with the correct ENV selected, CD to where you want to host your project. 

Create a new project folder and CD into it:
```
mkdir quant-test
cd quant-test
```
Create a new lean project in this location using the "LEAN Commands: 
```
lean create-project quant-test
```
![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/c08fb07f-b52b-4911-add9-f19eca0b3be8)

Open "VS Code" and open the newly created folder. You will see that a "main.py" file is automatically created. 
Make sure that the created ENV is the standard interpretor for the project 

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/69bcfc66-6e84-427f-98db-be98880e429a)

-----------------

## Lean Login 

Use the "Anaconda Prompt" and with the correct ENV selected, login with the command:
```
lean login
```
You will need to have an account with Quantconnect. Log into your account and click on profile name -> my account, then scroll down to security and click: "Request Email With Token and Your User-Id for API Requests"

You will be sent API details via your registered email. 

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/cd61d900-1e39-4691-8026-559a00c080c3)

Use these details at the prompts:

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/4c374967-72f1-422b-88ff-394f7f12eaf3)

-----------------

## Lean Init 

The code needs to be initialized and this is performed in the  "Anaconda Prompt", navigate to your project file and use the command: 
```
lean init
```
As the directory is not empty, you will need to confirm "y" to continue
This will download sample data to the project. 

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/464115ee-ba4a-45e6-b6ce-ba41c7435c90)

If you open VS Code you will see the newly created data included in your project now:

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/09fcb75b-076a-4eb5-bdb0-8044f12d9766)


-----------------


## Edit file in VS

Edit the python code in "VS Code"

(can add specific info here later)


-----------------


## Backtest the project 

Use the "Anaconda Prompt" and with the correct ENV selected, run the back test with the command: 
```
lean backtest quant-test
```

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/fd1ea0e3-8855-46ce-8d2a-ebc430b8cef6)


If you open VS Code, the results can be found in the backtest folder, timestamped to when the test was run. 

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/3d4d3c8e-2760-4439-9d52-ed3306af3ba0)


-----------------


## Push project to cloud and backtest

You can also run the back tests on cloud server to see better information by:
```
lean cloud backtest --push "quant-test"
```
This will provide extra information

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/324b43e2-a3ee-412e-86de-ed2d2082801c)


-----------------


## See backtest on cloud format

You can run the back test on cloud, and see the results on the browser. You NEED to push the latest code to the cloud before running this command. 
```
lean cloud backtest --open "quant-test"
```

![image](https://github.com/FlatFaceCat/QuantConnect-Local-Setup-Guide/assets/80037958/19e7032f-fa81-4e5c-8f9a-4bc4345f909a)


