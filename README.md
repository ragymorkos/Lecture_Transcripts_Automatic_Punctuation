Note 1: this repository is not being actively maintained or improved at the moment, but I am quick to respond if you find a bug and open a ticket on GitHub or email me.

Note 2: Because some videos have manually edited and punctuated subtitles uploaded alongside the video, it can be worth it to check if those are available first. You can check the settings (accessed via the gear icon) for the YouTube video to see if they are available. You can also try to execute `youtube-dl --all-subs --skip-download <YouTube_link>` and you will either get the manually punctuated subtitles (in all available languages) if they exist or an error message saying "WARNING: video doesn't have subtitles".

# Intro

This repository contains a tool to provide automatic punctuation of lecture transcripts obtained from YouTube. YouTube's transcripts are automatically generated by Google's automatic speech recognition (ASR) functionality, but are not punctuated. My tool is specially configured to punctuate lecture transcripts, since transcripts can be helpful to learners for a variety of reasons. The tool's current average F-score for correctly punctuating transcripts of lecture videos using commas, periods, question marks and semicolons is 67.3. Note that this F-score will probably be much lower if you try my tool on non-lecture or non-educational videos as the context will be different.

My work on this tool slightly builds upon that of https://github.com/ottokart/punctuator2, from which my repository is forked. I used the training structure in that repository to train a customized bidirectional recurrent neural network on manually punctuated transcripts scraped from Udacity's YouTube channel (https://www.youtube.com/user/Udacity) and from Princeton's COS226 class on Coursera (https://www.coursera.org/learn/algorithms-part1/ and https://www.coursera.org/learn/algorithms-part2). The training data that was used can be found in the "training_data" subdirectory inside the root of this repository. For more information and details regarding the background and methodology for training the neural network and regarding the project in general, including possible ways to improve the F-score, please refer to the "final_report.pdf" file in the root of the repository. Please note that some of the things in the report might be outdated or irrelevant to this repository's functionality.

You can find the training data used in here: https://drive.google.com/drive/folders/1mmrD1Rk4xdeatwDv2zYe-TTjIR-Hor7V

# Requirements (Ubuntu)

* Python 2.7+
* pip (if it is not installed on your system, install with `sudo apt install python-pip`)
* Theano (if it is not installed on your system, install with `sudo pip install Theano`)
* youtube-dl (if it is not installed on your system, install with `sudo apt install youtube-dl`)
* ffmpeg (if it is not installed on your system, install with `sudo apt install ffmpeg`)
* The neural network file: download the file then place it in the root directory of the repository: https://drive.google.com/file/d/1AyBk8NHyOuf_JgKo0AUeZr_O0w9PJD2a

I have not yet tested this repository on a non-Linux OS. Feel free to send me the installation instructions or put a pull request on the readme if you were to make it work on MacOS or Windows.

# Usage

If you have a link to a YouTube lecture video or playlist, simply execute `python lecture_punctuator.py <YouTube_link>`, where `<YouTube_link>` could be the link of a YouTube video, playlist, or channel. The program will output the transcript(s) in the current working directory to a subdirectory called "transcripts". Please make sure that the path to `lecture_punctuator.py` is configured correctly. The output format for a transcript is `<Video Title>_<YouTube ID>`.
