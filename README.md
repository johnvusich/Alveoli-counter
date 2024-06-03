# Alveoli-counter

This script analyzes alveoli counts in whole mount images. It subsamples multiple areas from each image, counts the alveoli, and performs statistical analysis and visualization.

## Requirements

- Python 3.x
- `opencv-python`
- `numpy`
- `pandas`
- `scipy`
- `matplotlib`
- `seaborn`

## Installation

Install the required packages using pip:

```
pip install opencv-python numpy pandas scipy matplotlib seaborn
```


## Usage

To run the script, use the following command:
```
python analyze_alveoli.py --image_dir <IMAGE_DIRECTORY> --group1 <GROUP1_NAME> --group2 <GROUP2_NAME> --colors <GROUP1_COLOR> <GROUP2_COLOR> [OPTIONS]
```


### Arguments

- `--image_dir`: Directory containing the images (required).
- `--group1`: Name of the first comparison group (required).
- `--group2`: Name of the second comparison group (required).
- `--colors`: Colors for the groups in the plot (required). Provide two color values (e.g., `"#90EE90" "#0000FF"`).
- `--subsample_size`: Size of the subsample in pixels (default: 500).
- `--subsample_positions`: Subsample positions as a list of (x, y) pairs (default: `[100, 100, 300, 100, 500, 100]`).
- `--start_x`: Starting x-coordinate for subsampling (default: 100).
- `--start_y`: Starting y-coordinate for subsampling (default: 100).

### Example

To analyze images in the directory `path_to_images`, with comparison groups `CKO` and `NC`, and using colors `#90EE90` for `CKO` and `#0000FF` for `NC`, run the following command:
```
python analyze_alveoli.py --image_dir "path_to_images" --group1 "CKO" --group2 "NC" --colors "#90EE90" "#0000FF"
```

### Output

The script will produce the following outputs:
- `alveoli_counts_by_condition.csv`: CSV file containing alveoli counts for each sample, grouped by condition.
- `summary_statistics_alveoli.csv`: CSV file containing summary statistics for each group, including mean count, standard error, and p-value.
- `alveoli_counts_publication_quality.png`: A publication-quality plot with boxplots and individual points, saved as a PNG file.

### Example Outputs

Example of `alveoli_counts_by_condition.csv`:
```
Sample,Condition,Alveoli Count
sample1_CKO_PD5.tif,CKO,100
sample2_CKO_PD5.tif,CKO,120
sample1_NC_PD5.tif,NC,90
sample2_NC_PD5.tif,NC,110
```

Example of `summary_statistics_alveoli.csv`:
```
Condition,Mean Count,Standard Error,p-value
CKO,110,10,0.05
NC,100,10,0.05
```


### Plot

The resulting plot `alveoli_counts.png` will look like this:

![Alveoli Counts by Condition](alveoli_counts_publication_quality.png)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
