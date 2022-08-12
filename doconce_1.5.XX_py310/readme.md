NOTE update environment-yml with desired doconce version!

Changelog:
* added make relative to 1.5.11_py39
* added pdflatex relative to 1.5.12_py39
* added these relative to 1.5.13_py39 so all tests can be run
  - ispell
  - pandoc
  - locales
  - pytest
  - sphinx and sphinx_bootstrap_theme
  - bash_kernel
* changed to python 3.10 relative to 1.5.14

Still missing:
* Jupyter kernels
  - Julia kernel
  - R kernel

Notes:
* When running `python tests.py` from the docker container, run this first
  `sudo locale-gen nb_NO.UTF-8;  sudo update-locale`
  (this is needed for compiling `locale.do.txt`)
