from pydub import AudioSegment



# Load the audio file

audio_path = "/mnt/data/Screenrecorder-2024-08-07-13-13-32-575.mp3"

audio = AudioSegment.from_mp3(audio_path)



# Filter out frequencies that are typically associated with human speech (around 300 Hz to 3000 Hz)

# This is a rough approach to emphasize the beat, though it may not fully remove vocals depending on the mix.

low_pass_filter = audio.low_pass_filter(200)  # Keep the lower frequencies (bass and beat)

high_pass_filter = low_pass_filter.high_pass_filter(1000)  # Remove the frequencies that could contain vocals



# Save the processed audio

output_path = "/mnt/data/beat_only_output.mp3"

high_pass_filter.export(output_path, format="mp3")



output_path
