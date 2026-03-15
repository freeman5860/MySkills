---
description: Merge multiple video files into one using ffmpeg
trigger: When user wants to merge, concatenate, or combine multiple videos into a single file
---

# Merge Videos

Merge multiple video files into a single video file using ffmpeg.

## Prerequisites

- ffmpeg must be installed on the system
- Check with: `which ffmpeg`
- Install on macOS: `brew install ffmpeg`
- Install on Ubuntu: `sudo apt install ffmpeg`

## Instructions

When the user provides video files to merge:

1. **Verify files exist**
   ```bash
   ls -la "path/to/video1.mp4" "path/to/video2.mp4" ...
   ```

2. **Verify ffmpeg is available**
   ```bash
   which ffmpeg
   ```

3. **Create a temporary file list**
   ```bash
   cat > /tmp/videos.txt << 'EOF'
   file '/absolute/path/to/video1.mp4'
   file '/absolute/path/to/video2.mp4'
   file '/absolute/path/to/video3.mp4'
   EOF
   ```

   Note: Use absolute paths and handle spaces in filenames properly.

4. **Merge videos with ffmpeg**
   ```bash
   ffmpeg -f concat -safe 0 -i /tmp/videos.txt -c copy "output_path/merged_video.mp4" -y 2>&1
   ```

   Parameters explained:
   - `-f concat`: Use concat demuxer
   - `-safe 0`: Allow absolute paths
   - `-i /tmp/videos.txt`: Input file list
   - `-c copy`: Copy streams without re-encoding (fast)
   - `-y`: Overwrite output file if exists

5. **Report results** including:
   - Output file path
   - Duration
   - Resolution
   - File size
   - Merge order

## Output Location

- Default: Same directory as input files
- Filename: `merged_video.mp4`
- User can specify custom output path

## Handling Different Codecs

If videos have different codecs/resolutions, use re-encoding instead:

```bash
ffmpeg -f concat -safe 0 -i /tmp/videos.txt -c:v libx264 -c:a aac "output.mp4" -y
```

This is slower but ensures compatibility.

## Example Usage

User input:
```
/merge-videos /path/to/video1.mp4 /path/to/video2.mp4 /path/to/video3.mp4
```

Or natural language:
```
帮我把这三个视频合并成一个：
/Users/xxx/Downloads/1.mp4
/Users/xxx/Downloads/2.mp4
/Users/xxx/Downloads/3.mp4
```

## Error Handling

- If ffmpeg is not installed, provide installation instructions
- If files don't exist, list which files are missing
- If merge fails due to codec mismatch, suggest re-encoding approach
- Always clean up temporary files after completion

## Notes

- Videos are merged in the order provided
- For best results, input videos should have the same codec, resolution, and frame rate
- The `-c copy` option is fast as it doesn't re-encode, but requires compatible input formats
