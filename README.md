# Dav-py-clean
Deep cleaning of mai-tai pulsed laser two-photon kinetic stability experimental data
import pandas as pd

filenames = [
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00000.txt',
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00001.txt',
    # Add more filenames here...
]

# Create an empty DataFrame to store the contents of each file
data = pd.DataFrame()

# Read each file and concatenate its contents into a new column
for filename in filenames:
    with open(filename, 'r') as file:
        column_name = filename.split('/')[-1].split('.')[0]  # Extracting column name from file path
        data[column_name] = [line.strip() for line in file]

# Write the concatenated data to an Excel file
output_excel_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.xlsx'
data.to_excel(output_excel_path, index=False)


filenames = [
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00000.txt',
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00001.txt',
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00002.txt',
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00003.txt',
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00004.txt',
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00005.txt',
    'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/P192_toluene_kineticscan00006.txt',
    

    # Add more filenames here...
]

output_file_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.txt'

with open(output_file_path, 'w') as writer:
    readers = [open(filename) for filename in filenames]
    for lines in zip(*readers):
        concatenated_lines = [' '.join([line.strip() for line in lines])]
        writer.write('\t'.join(concatenated_lines) + '\n')  # Separate columns with a tab (or any other suitable delimiter)

with open(output_file_path, 'r') as file:
    for line in file:
        parts = line.strip().split(',') # Split by comma (,)
        if len(parts) >= 2:
            print(parts[0], parts[1])
        else:
            print("Error: Not enough columns in line:", line)
import csv

input_file_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.txt'
output_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.csv'

# Open the input tab-separated text file and the output CSV file
with open(input_file_path, 'r') as input_file, open(output_csv_path, 'w', newline='') as output_csv:
    # Create a CSV writer object
    csv_writer = csv.writer(output_csv)
    
    # Read each line from the input text file, split it by space, and write it to the CSV file
    for line in input_file:
        row = line.strip().split()  # Split the line by space delimiter
        csv_writer.writerow(row)  # Write the row to the CSV file

import csv
import re

input_file_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.txt'
output_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.csv'

# Open the input tab-separated text file and the output CSV file
with open(input_file_path, 'r') as input_file, open(output_csv_path, 'w', newline='') as output_csv:
    # Create a CSV writer object
    csv_writer = csv.writer(output_csv)
    
    # Read each line from the input text file, filter out non-numeric elements, and write it to the CSV file
    for line in input_file:
        # Remove all non-numeric characters from the line using regular expression
        numbers_only = re.findall(r'[\d.]+', line)
        # Write the row to the CSV file
        csv_writer.writerow(numbers_only)

input_file_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.txt'
output_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.csv'

# Open the input tab-separated text file and the output csv file
with open(input_file_path, 'r') as input_file, open (output_csv_path, 'w', newline='') as output_csv:
    # Create a CSV writer object
    csv_writer = csv.writer(output_csv)

    # Skip the first 17 rows
    for _ in range(17):
        next(input_file)

    # Read each line from the input text file, filter out non-numeric elements, and write it to the csv file
    for line in input_file:
        # Remove all non-numeric characters from the line using regular expression
        numbers_only = re.findall(r'[\d.]+', line)

        # Insert two empty columns after every two columns
        processed_row = []
        for i, num in enumerate(numbers_only):
            processed_row.append(num)
            if (i + 1) % 2 == 0: # Check if this is the end of every two columns
                processed_row.extend(['', '']) # Add two empty columns
            
        # Write the row to the CSV file
        csv_writer.writerow(processed_row)

input_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.csv'
new_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/correction_file.csv'

# Read the input and new CSV files
try:
    input_df = pd.read_csv(input_csv_path, header=None)  # Assuming no headers
    new_df = pd.read_csv(new_csv_path, header=None)  # Assuming no headers

    # Select the first column from new_csv
    first_column_new = new_df.iloc[:, 0]

    # Find the indices of the columns where the data should be pasted
    paste_column_indices = [2]  # Paste into the third column initially
    start_column_index = 6
    paste_column_indices += [start_column_index + i * 4 for i in range(len(input_df.columns[start_column_index:]))]

    # Filter out the indices that exceed the number of columns in input_df
    paste_column_indices = [idx for idx in paste_column_indices if idx < len(input_df.columns)]

    # Paste the first column from new_csv into the selected columns
    for idx in paste_column_indices:
        input_df.iloc[:, idx] = first_column_new

    # Write the modified DataFrame back to the input CSV file
    input_df.to_csv(input_csv_path, index=False, header=False)

    print("Data copied and pasted successfully.")

except FileNotFoundError:
    print("File not found. Please check the input CSV file paths:", input_csv_path, new_csv_path)
except Exception as e:
    print("An error occurred:", e)

input_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.csv'

# Read the input CSV file
try:
    input_df = pd.read_csv(input_csv_path, header=None)

    # Find the indices of the empty columns
    empty_column_indices = [i for i, col in enumerate(input_df.columns) if input_df[col].isnull().all()]

    # Iterate over the DataFrame and process each group of three columns
    for i in range(0, len(input_df.columns), 4):
        # Calculate the indices of A, B, and C columns in the current group
        a_idx = i
        b_idx = i + 1
        c_idx = i + 2

        # Check if there are at least two filled columns in the group
        if b_idx < len(input_df.columns) and c_idx < len(input_df.columns):
            # Perform the division for the current group and store the result in the corresponding D column
            input_df[i + 3] = input_df[b_idx] / input_df[c_idx]

    # Write the modified DataFrame back to the input CSV file
    input_df.to_csv(input_csv_path, index=False, header=False)

    print("Division completed successfully.")

except FileNotFoundError:
    print("File not found. Please check the input CSV file path:", input_csv_path)
except Exception as e:
    print("An error occurred:", e)

input_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated.csv'

# Read the input CSV file
try:
    input_df = pd.read_csv(input_csv_path, header=None)

    # Select the first A column and all D columns
    selected_columns = [0]  # First A column
    for i, col in enumerate(input_df.columns):
        if i % 4 == 3:  # Select all D columns
            selected_columns.append(i)

    # Create a new DataFrame with selected columns
    new_df = input_df.iloc[:, selected_columns]

    # Write the new DataFrame to a new CSV file
    new_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated_corrected.csv'
    new_df.to_csv(new_csv_path, index=False, header=False)

    print("Selected columns copied to new sheet successfully.")

except FileNotFoundError:
    print("File not found. Please check the input CSV file path:", input_csv_path)
except Exception as e:
    print("An error occurred:", e)

output_csv_path = 'C:/VT_PL/P192_2PAstability_toluene_100uM/OneDrive_2024-02-14/13.02.2024_ P192 toluene stability over 6 h/output_concatenated_corrected.csv'

# Read the existing CSV file
try:
    output_df = pd.read_csv(output_csv_path, header=None)

    # Calculate the number of existing columns
    num_columns = len(output_df.columns)

    # Generate headers for the existing columns
    headers = ['Wavelength']
    for i in range(1, num_columns):
        headers.append(f'{(i - 1) * 3} mins')

    # Insert the new row at the beginning of the DataFrame
    output_df.loc[-1] = headers
    output_df.index = output_df.index + 1  # Shift the index
    output_df = output_df.sort_index()

    # Write the modified DataFrame back to the CSV file
    output_df.to_csv(output_csv_path, index=False, header=False)

    print("Header row added successfully.")

except FileNotFoundError:
    print("File not found. Please check the output CSV file path:", output_csv_path)
except Exception as e:
    print("An error occurred:", e)

