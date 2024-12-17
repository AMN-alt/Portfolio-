EEG Data Graph

```python
for session_index, session in enumerate(spike_trains_3d):
    fig, axs = plt.subplots(1, 2, figsize=[10, 3])

    # draw a raster plot into first subplot, axs[0]
    # add shading for stimulus duration
    axs[0].axvspan(light_onset_time, light_offset_time, alpha=0.5, color='greenyellow')

    for trial in range(len(session)):
        spike_times = [i for i, x in enumerate(session[trial]) if x == spike_value]
        axs[0].vlines(spike_times, trial - 0.5, trial + 0.5)

    # Set x axis range so that time zero is more visible    
    axs[0].set_xlim([-1, len(session[0])])

    # specify tick marks and label y axis
    axs[0].set_yticks(range(len(session)))
    axs[0].set_ylabel('Trial Number')

    axs[0].set_title('Neuronal Spike Times') 

    
    # draw a PSTH into second subplot, axs[1]
    # add shading for stimulus duration
    axs[1].axvspan(light_onset_time, light_offset_time, alpha=0.5, color='greenyellow')

    # Draw the PSTH
    axs[1].bar(range(len(session[0])), 
               np.mean(session, 0)
               )

    # Use same x axis limits as for raster plot
    axs[1].set_xlim([-1, len(session[0])])

    # Add line showing chance probability of firing
    axs[1].axhline(y=0.5, xmin=0, xmax=20, linestyle='--', color='gray')

    # Make the plot pretty
    axs[1].set_title('Peri-Stimulus Time Histogram (PSTH)')
    axs[1].set_xlabel('Time (ms)')
    axs[1].set_ylabel('Probability of spike')


    ### Overall figure stuff
    fig.suptitle(f'Session {session_index + 1} Spike Trains Shown Two Ways')
    plt.tight_layout(pad=2)
    plt.show()```
