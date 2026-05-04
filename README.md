# vortex-tracker

OpenCV-based analysis script for measuring vortex ring diameter over time from image sequences.

Developed for IISc internship workflow experiments.

## What The Script Does

File: `vortex_tracker.py`

- Loads image frames from a folder
- Converts each frame to grayscale and blurred image
- Applies fixed binary thresholding
- Finds largest contour as vortex region
- Measures vertical diameter from topmost to bottommost contour points
- Converts pixels to centimeters using calibration constant
- Logs per-frame diameter measurements
- Plots diameter vs time (assuming fixed 500 FPS)

## Calibration and Inputs

Current constant:

- `PIXELS_PER_CM = 566 / 2.5`

Before running, set these paths in the script:

- `folder_path` - input image directory
- `project_folder` - output/log directory

## Outputs

- `vortex_diameters_log.txt`
- `vortex_Diameter_changes.png`
- optional append from `Diameter_of_vortex.txt` if present

The repo also includes sample assets/logs:

- frame images under `vortex_images/`
- historical speed and diameter logs
- generated diameter plots

## Run

```bash
python vortex_tracker.py
```

## Dependencies

```bash
pip install opencv-python numpy matplotlib
```

## Limitations

- Uses fixed thresholding tuned to specific capture conditions
- Assumes largest contour is always the vortex boundary
- Time axis assumes 500 FPS; adjust if your capture rate differs
- Requires manual path setup in script before execution

