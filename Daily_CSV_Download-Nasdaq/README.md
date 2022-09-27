# Daily CSV download project from website (nasdaq)
Created this script to
- Automatically download 
- Save to desired folder
- Rename the downloaded file

## To set this up to run automatically daily
- copy the code from the .ipynb file into a .py script
- Write a .bat file detailing where can windows find the file. Example as such
    - `C:\programs\python.exe "C:/Nasdaq_Daily_CSV_Download.py"
    pause`
- Configure Windows Task scheduler to run .bat file daily

You can reference this website for more information: [*source*](https://towardsdatascience.com/automate-your-python-scripts-with-task-scheduler-661d0a40b279)