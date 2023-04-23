# -MP3_format_to_WAV_format 
Please follow the instructions below to complete the task.

Instructions:

**1** : Install the required library 'pydub' by running the command 'pip install pydub' in the terminal.  
**2** : Create a Python file 'mp3_to_wav_converter.py' and copy the code below.  
**3** : In the terminal, navigate to the directory containing the 'mp3_to_wav_converter.py' file and run the command 'python mp3_to_wav_converter.py <input-folder> <output-folder>', where <input-folder> is the path to the folder containing MP3 files and <output-folder> is the path to the folder where the converted WAV files will be saved.  


import os
import sys
from pydub import AudioSegment

def convert_to_wav(input_file, output_folder):
    sound = AudioSegment.from_mp3(input_file)
    output_file = os.path.join(output_folder, os.path.splitext(os.path.basename(input_file))[0] + '.wav')
    sound.export(output_file, format="wav")

def main():
    input_folder = sys.argv[1]
    output_folder = sys.argv[2]

    if not os.path.isdir(input_folder):
        print('Input folder not found.')
        return

    if not os.path.isdir(output_folder):
        os.makedirs(output_folder)

    for filename in os.listdir(input_folder):
        if filename.endswith('.mp3'):
            input_file = os.path.join(input_folder, filename)
            convert_to_wav(input_file, output_folder)

    print('Conversion complete.')

if __name__ == '__main__':
    main()
