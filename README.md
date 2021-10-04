# To-convert-an-audio-file-into-another-format
%To convert an audio file into another format eg from wav to mp3

This code makes use of the functions:
audioread - to read in the audio file 
fopen - to create a new file 






%To convert an audio file into another format
% Example convert a wav into a '.dat' format for use in OrCAD Pspice simulation program.


%load the file using audioread, use the file directory eg audioread('C:/users/admin/speech_dft.wav');
% or load the file into the MATHLAB folder as done below 
[x,fs]=audioread('speech_dft.wav');
% This saves the sampling frequency to fs and audio signal to x  

%To plot the audio signal 
t=(0:1:length(x)-1)*45e-6; % Time axis aprox 1/fs
t=t'; % Transpose
plot(t,x);%plot the input audio signal 


speech_data=[t x]; % Save data to be moved into new file format 

%Create a new file using fopen function
%name the file with it format, here its called 'speech' and is a 'dat' file fomat. 
fid=fopen('speech.dat','w'); 

%print the data onto the newly created file
fprintf(fid,'%8.6f %8.6f\n',speech_data');
fclose(fid); % close the file 
