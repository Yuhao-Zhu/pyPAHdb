=====
Usage
=====

The general flow for using pypahdb is shown below. See the tutorial
series for a more in-depth walk-through.

.. code-block:: python

    import pkg_resources

    from pypahdb.decomposer import Decomposer
    from pypahdb.observation import Observation

    # A provided sample data file (in FITS format).
    file_path = 'data/sample_data_NGC7023.fits'
    data_file = pkg_resources.resource_filename('pypahdb', file_path)

    # Construct an Observation object.
    obs = Observation(data_file)

    # Pass the Observation's spectrum to Decomposer, which performs the fit.
    pahdb_fit = Decomposer(obs.spectrum)

    # Write the fit to file.
    pahdb_fit.save_pdf('NGC7023_pypahdb.pdf')
    pahdb_fit.save_fits('NGC7023_pypahdb.fits', header=obs.header)