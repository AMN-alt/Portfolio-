3D Array MRI Brain Slice Data Graphed Using Matplotlib, To Showcase The Internal Structure Of The Cortex Through Different Sliced Volume Segments  



```python
fig, axs = plt.subplots(fig_rows, fig_cols, figsize=[10, 10])

for idx, img in enumerate(range(start_stop, plot_range, step_size)):
    axs.flat[idx].imshow(brain_vol[img, :, :], cmap='gray')
    axs.flat[idx].axis('off')
        
plt.tight_layout()
plt.show()```

![image](https://github.com/user-attachments/assets/a33c209e-c1ef-4084-8218-2e18321cc0a5)
