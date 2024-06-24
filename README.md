# Extracting_Date_and_Time_from_File_Name
This Python script extracts the date and time information from a filename.
<br> The file name should be in a format - 'file example_20240619075612.avi'.</br>
Here the 'file example' is the name of the file if any.</br>
The number after the file name -'20240619075612', represents the date and time in a format - '2024-06-19 08:18:06'.
<br></br>

## Keep In Mind
The current implementation of the code is tailored to filenames in the format: '/path/to/file example_YYYYMMDDHHMMSS.ext'. If the format of the filenames changes, the code will need to be adjusted accordingly.

To adapt the code to different filename formats, you need to:
<br>
1. Update the way the base filename is extracted.
2. Modify how the timestamp string is identified and extracted.
3. Adjust the slicing for date and time extraction if the length or position of the timestamp changes.



## Explanation Of Code
The provided Python script processes a list of filenames that include embedded timestamps. It extracts the date, time, and a combined datetime object from each filename and then calculates the time differences between consecutive filenames. In the code provided, you can add n number of videos as required.</br>
Here’s a detailed explanation of the code:

### Step-by-Step Explanation

#### 1. List of Filenames

```python
filenames = [
    '/content/file example_20240619075612.avi',
    '/content/file example_20240619081806.avi',
    # Add more filenames as needed
]
```
- The list filenames contains the filenames that include timestamps. These filenames are examples and can be replaced with actual filenames.

#### 2. Function Definition

```python
def extract_date_time_and_datetime(filename):
    base_filename = filename.rsplit('.', 1)[0]
    parts = base_filename.split('_')
    datetime_str = parts[-1]

    date = datetime_str[:8]  
    time = datetime_str[8:]  

    dt = datetime.strptime(datetime_str, '%Y%m%d%H%M%S')

    return date, time, dt
```
- `extract_date_time_and_datetime` is a function that takes a filename as input.
- `base_filename = filename.rsplit('.', 1)[0]` removes the file extension.
- `parts = base_filename.split('_')` splits the filename at underscores.
- `datetime_str = parts[-1]` extracts the last part, which is the datetime string.
- `date = datetime_str[:8]` extracts the date part (first 8 characters).
- `time = datetime_str[8:]` extracts the time part (remaining characters).
- `dt = datetime.strptime(datetime_str, '%Y%m%d%H%M%S')` converts the string into a datetime object.
- The function returns the date, time, and datetime object.

#### 3. Initialization of Lists

```python
dates = []
times = []
datetimes = []
```
- These lists will store the extracted dates, times, and datetime objects respectively.

#### 4. Extraction Loop

```python
for filename in filenames:
    date, time, dt = extract_date_time_and_datetime(filename)
    dates.append(date)
    times.append(time)
    datetimes.append(dt)
```
- This loop iterates through each filename, extracts the date, time, and datetime using the defined function, and appends them to the respective lists.

#### 5. Printing Extracted Information

```python
for i, filename in enumerate(filenames):
    file_num = i + 1
    print(f"File{file_num}:")
    print("Date:", dates[i])
    print("Time:", times[i])
    print("Datetime:", datetimes[i])
    print()
```
- This loop prints the extracted information for each filename in a readable format.

#### 6. Calculating Time Differences

```python
for i in range(len(filenames) - 1):
    file_num1 = i + 1
    file_num2 = i + 2
    time_difference = datetimes[i+1] - datetimes[i]
    print(f"Time Difference between File{file_num1} and File{file_num2}: {time_difference}")
```
- This loop calculates and prints the time differences between consecutive datetime objects, showing the differences in a human-readable format.

##
This script is useful for analyzing video files or other files that have timestamps embedded in their filenames, making it easier to track when each file was created or modified.

##
I hope this explanation was helpful to you.</br>
Thank you for your support.</br>
Keep Learning.</br>
~Pranjali Goyal</br>















