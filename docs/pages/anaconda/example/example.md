---
title: Step-by-Step Example
nav_order: 1
parent: Anaconda Environment Management
---

# Step-by-Step Example
This section shows a step-by-step example of how to download Anaconda, set up an environment, begin working with the environment, and run MyoSim.

1.	Download GitHub Desktop and follow installation instructions by visiting https://desktop.github.com/ and clicking the “Download for Windows” button.

 ![How to picture #1](../../../assets/images/anaconda/howto_1.png)

2.	Launch GitHub Desktop through the Start Menu.

![How to picture #2](../../../assets/images/anaconda/howto_2.png)

3.	Sign into your GitHub account when prompted.
4.	Click “File” then click “Clone Repository”.

 ![How to picture #3](../../../assets/images/anaconda/howto_3.png)

5.	Clone the Python_MyoSim repository.

![How to picture #4](../../../assets/images/anaconda/howto_4.png) 

6.	Download Anaconda - Go to https://www.anaconda.com/distribution/ and download the Python 3.7 version of Anaconda after clicking the “Windows” button.

![How to picture #5](../../../assets/images/anaconda/howto_5.png) 

7.	Follow the installation instructions prompted by the Anaconda installer and accept all default options.
8.	Launch the Anaconda Prompt from the Start Menu.

![How to picture #6](../../../assets/images/anaconda/howto_6.png)

9.	Type `conda create –name <NAME_OF_YOUR_ENVIRONMENT>` where `<NAME_OF_YOUR_ENVIRONMENT>` is the name of the environment you would like to create. In this example, I’ve chosen `example_environment`. Type `y` for “yes” when you’re prompted to and hit <kbd>Enter</kbd> on your keyboard.

![How to picture #7](../../../assets/images/anaconda/howto_7.png)

10.	Launch the Anaconda Navigator from the Start Menu.

![How to picture #8](../../../assets/images/anaconda/howto_8.png)

11.	 Change into the created environment by selecting it from the drop-down menu in the Anaconda Navigator.

![How to picture #9](../../../assets/images/anaconda/howto_9.png)

12.	Click the “Environments” button on the left panel of the Anaconda Navigator.

![How to picture #10](../../../assets/images/anaconda/howto_10.png)

13.	Change the package view to “Not Installed” by selecting it from the drop-down menu.

![How to picture #11](../../../assets/images/anaconda/howto_11.png)

14.	Search for and click the check box of numpy package.

![How to picture #12](../../../assets/images/anaconda/howto_12.png)

15.	Repeat step 14 for the following packages: “pandas”, “matplotlib”, “scipy”. 
16.	Click “Apply” on the bottom left of the screen and proceed through the prompts.
17.	Navigate back to “Home”.

![How to picture #13](../../../assets/images/anaconda/howto_13.png)

18.	Install Spyder and Jupyter Notebook by clicking “Install” for both applications.

![How to picture #14](../../../assets/images/anaconda/howto_14.png)

19.	Launch Spyder through the same Anaconda Navigator window after installation.

![How to picture #15](../../../assets/images/anaconda/howto_15.png)

20.	Begin coding.