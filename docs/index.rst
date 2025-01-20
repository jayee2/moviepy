from moviepy.editor import *

# Define paths to the images
image1_path = "path_to_image1.jpg"
image2_path = "path_to_image2.jpg"

# Load the images as video clips
image1 = ImageClip(image1_path).set_duration(4).resize(height=720)
image2 = ImageClip(image2_path).set_duration(4).resize(height=720)

# Define text content for the video
texts = [
    ("Unlock the Power of Numerology\nwith a Personalized Report!", 4),
    ("Discover Your Human Nature:\nTrue self and hidden traits.", 4),
    ("Career & Business:\nPath to success and prosperity.", 4),
    ("Marriage Compatibility:\nEnhance harmony with your partner.", 4),
    ("Love & Relationships:\nBuild stronger, meaningful connections.", 4),
    ("Remedies:\nOvercome challenges and attract positivity.", 4),
    ("\u2728 Transform Your Life Today!", 4),
    ("\ud83d\udc49 Book Your Report Now!", 4)
]

# Create text clips and combine them with images
text_clips = []
for i, (text, duration) in enumerate(texts):
    text_clip = TextClip(
        text,
        fontsize=50,
        color="gold",
        font="Arial-Bold",
        bg_color="black",
        size=(1280, None)
    ).set_duration(duration).set_position("center")

    if i % 2 == 0:
        combined_clip = CompositeVideoClip([image1, text_clip.set_position(("center", "bottom"))])
    else:
        combined_clip = CompositeVideoClip([image2, text_clip.set_position(("center", "bottom"))])

    text_clips.append(combined_clip)

# Concatenate all the clips to form the final video
final_video = concatenate_videoclips(text_clips, method="compose")

# Output video file
output_file = "NumerologyGyan_Promo.mp4"
final_video.write_videofile(output_file, fps=24, codec="libx264", audio=False)

# Instructions:
# 1. Replace "path_to_image1.jpg" and "path_to_image2.jpg" with the actual paths to your images.
# 2. Run this script in a Python environment with MoviePy installed.
# 3. The resulting video will be saved as "NumerologyGyan_Promo.mp4" in the current working directory.
