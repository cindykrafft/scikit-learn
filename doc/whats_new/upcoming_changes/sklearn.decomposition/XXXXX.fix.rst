- :class:`decomposition.PCA` with `svd_solver="covariance_eigh"` (selected by
  `svd_solver="auto"` for dense data with at most 1000 features and at least ten
  times as many samples) now accumulates the covariance of centered row batches
  instead of centering `X.T @ X` post hoc, so features with a large common offset
  no longer lose their variance to rounding (the explained variance was 33 % off
  for float32 values around 100 and 1.7 % off for float64 values around 1e6, and
  meaningless beyond).
  By :user:`Cindy Krafft <cindykrafft>`.
