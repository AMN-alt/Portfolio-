A For Loop Used To Clean Up 3D Arrays Of Action Spike EEG Data, By Specifically Identifying And Excluding Indices With Values Not Equal To 0 Or 1


```python
[[[index for index, value in enumerate(spike_train) if value not in [0, 1]] for spike_train in session] for session in spike_trains_3d]```
