.. image:: images/orochi_icon.png
   :align: center
   :width: 80px
   :target: https://Tominaka-Laboratory.github.io/orochi
   :alt: Orochi Logo

======
orochi
======

.. |title| replace:: orochi
.. _title: https://Tominaka-Laboratory.github.io/orochi

.. |Icon| image:: images/orochi_icon.png
   :target: https://Tominaka-Laboratory.github.io/orochi
   :height: 100px

|PyPi| |PythonVersion| |PR| |ChemRxiv|

|CI| |Codecov| |Black| |Tracking|

.. |ChemRxiv| image:: https://img.shields.io/badge/ChemRxiv-Preprint-blue
     :target: https://chemrxiv.org/doc/d84591ff-85b9-489c-839a-4f7170dcc1c4

.. |Black| image:: https://img.shields.io/badge/code_style-black-black
     :target: https://github.com/psf/black

.. |CI| image:: https://github.com/Tominaka-Laboratory/orochi/actions/workflows/tests.yml/badge.svg
     :target: https://github.com/Tominaka-Laboratory/orochi/actions/workflows/tests.yml

.. |Codecov| image:: https://codecov.io/gh/Tominaka-Laboratory/orochi/branch/main/graph/badge.svg
     :target: https://codecov.io/gh/Tominaka-Laboratory/orochi

.. |PR| image:: https://img.shields.io/badge/PR-Welcome-29ab47ff

.. |PyPi| image:: https://img.shields.io/pypi/v/orochi
     :target: https://pypi.org/project/orochi/

.. |PythonVersion| image:: https://img.shields.io/pypi/pyversions/orochi
     :target: https://pypi.org/project/orochi/

.. |Tracking| image:: https://img.shields.io/badge/issue_tracking-github-blue
     :target: https://github.com/Tominaka-Laboratory/orochi/issues

---
Orochi: An Ecosystem Framework for Parameter Management in Scientific Computing
---

The **Orochi** framework draws inspiration from the legendary Japanese eight-headed serpent, **Yamata no Orochi**. Just as the mythical creature's heads and tails emanate from a powerful central body, the Orochi Python packages are designed around a **unified core for parameter management**, enabling the coordinated operation of diverse functionalities. At its heart, ``orochi.base`` acts as this central "body," from which specialized modules branch out like distinct "heads," each leveraging the core's robust parameter system.

Orochi is a comprehensive **ecosystem framework** crafted to streamline **parameter management** in scientific and technological computing, from internal calculations to external module interactions and UI construction. It offers a powerful environment to define, manipulate, and share parameters across various scientific tasks, facilitating advanced workflows and visualization, often through intuitive web-based interfaces.

**Parameter management** is a critical element in scientific computing. It's not just about simple variables; parameters are essential for controlling internal computations, defining the behavior of complex simulations, and enabling seamless data exchange with external modules. In the rapidly evolving fields of Artificial Intelligence and Machine Learning, the ability to actively connect and collaborate with external modules via shared parameters (often treated as data or metadata) is paramount. Orochi is specifically designed to simplify this intricate process.

One of Orochi's key strengths lies in its design: by simply **inheriting from core ``orochi`` classes**, you can easily build complex applications with **robust parameter management** (including support for black-box optimization and machine learning workflows) and **seamless inter-module integration**. While UI development often becomes cumbersome for advanced programs, Orochi simplifies this significantly. It allows you to **Pythonically create distinct interfaces for each task**, largely by providing parameters to the user, with UI elements derived directly from these managed parameters.

Currently, the primary focus of Orochi's development is **material structure analysis**, though its underlying principles are broadly applicable across scientific domains.

The Orochi framework is composed of specialized, modular packages working in concert:

* **``orochi.base`` (The Core for Parameters)**: The foundational package for **unified and robust parameter management**. It provides a standardized system for defining, accessing, and modifying parameters, ensuring hierarchical consistency and cross-module synchronization.

* **``orochi.pixia`` (2D Detector Data Reduction)**: Advanced 2D area detector data processing, instrumental geometry calibration (beam center, sample-to-detector distance, detector tilts), and automated diagonal sector integration avoiding orthogonal edge cutoffs to access maximum momentum transfer *Q_max*.

* **``orochi.pdfget`` (1D Total Scattering Reduction)**: Rigorous 1D total scattering data reduction, transforming experimental diffraction profiles into the total structure factor *S(Q)*, reduced structure factor *F(Q)*, and pair distribution function *G(r)* using the Faber–Ziman formalism with automated polynomial low-*r* ripple suppression.

* **``orochi.phase`` (Structure & Crystallography Management)**: Manages atomic coordinates, anisotropic directional periodic boundary conditions (1D/2D/3D), Wyckoff symmetry, and coordination-preserving explicit nanoparticle shape envelopes.

* **``orochi.pdfsim`` (Real-Space PDF Simulation)**: High-performance calculation of Pair Distribution Functions *G(r)* from structural models, featuring exact *Q*-dependent complex scattering factors via DCT convolution, low-dimensional baseline density filtering, and Numba acceleration.

* **``orochi.fit`` (Parameter Refinement & Optimization Engine)**: Robust structural refinement against experimental scattering data, supporting bounded least-squares fitting (via lmfit/SciPy) and Bayesian global optimization (via Optuna).

* **``orochi.ui`` (Interactive User Interface)**: Generates intuitive, parameter-driven Gradio web GUIs with interactive 3D crystal/nanoparticle visualization, live residual plotting, and unified lesson notes.

* **``orochi.pipeline`` (Automated End-to-End Workflows)**: Orchestrates complete data reduction and structural refinement workflows from raw 2D detector images to final structural models in automated scripts.

* **``orochi.tutorial`` (Self-Contained Reproducible Tutorials)**: Comprehensive tutorials and benchmark workflows reproducing the figures and quantitative results of the Orochi publication.

* **``orochi.view`` (3D Model Visualization)**: Interactive 3D molecular and crystallographic structure visualization for nanoparticles, crystal unit cells, and 2D nanosheets.

Orochi aims to empower researchers and developers to quickly build complex scientific applications with sophisticated parameter control and custom UIs, allowing them to focus on the scientific logic rather than implementation complexities.

---------------
Getting Started
---------------

To begin using the Orochi framework, follow these steps to install the primary ``orochi`` meta-package and learn how to run the interactive tutorials.

### Installation

The preferred method is to use **Miniconda Python** and install from the "conda-forge" channel of Conda packages.

To add "conda-forge" to the conda channels, run the following in a terminal:

::

    conda config --add channels conda-forge

We want to install our packages in a suitable conda environment. The following creates and activates a new environment named ``orochi_env``:

::

    conda create -n orochi_env orochi
    conda activate orochi_env

To confirm that the installation was successful, type:

::

    python -c "import orochi; print(orochi.__version__)"

The output should print the latest version displayed on the badges above.

If the above does not work, you can use ``pip`` to download and install the latest release from the Python Package Index. To install using ``pip`` into your ``orochi_env`` environment, type:

::

    pip install orochi

---
**Installing Individual Packages**

Sub-packages can also be installed individually using ``pip``:

::

    pip install orochi.base orochi.pixia orochi.pdfget orochi.phase orochi.pdfsim orochi.fit orochi.ui orochi.pipeline orochi.tutorial orochi.view

---

If you prefer to install from local source trees, clone the repositories and run the following in development mode:

::

    pip install -e ./orochi.base -e ./orochi.pixia -e ./orochi.pdfget -e ./orochi.phase -e ./orochi.pdfsim -e ./orochi.fit -e ./orochi.ui -e ./orochi.pipeline -e ./orochi.tutorial -e ./orochi.view 

### Running Tutorials

Official, self-contained tutorials reproducing the scientific results, figures, and benchmark refinements of the Orochi publication are provided in the ``orochi.tutorial`` package (`https://github.com/Tominaka-Laboratory/orochi.tutorial <https://github.com/Tominaka-Laboratory/orochi.tutorial>`_).

To run any tutorial in headless command-line (CUI) mode:

::

    python tutorials/00_ni_synchrotron_benchmark/run_tutorial.py
    python tutorials/01_ceo2_reduction_and_qdepend/run_tutorial.py
    python tutorials/02_ceo2_nanoparticle_explicit_vs_analytical/run_tutorial.py
    python tutorials/03_pto2_nanosheet_2d_pbc/run_tutorial.py

To launch interactive Gradio web interfaces with 3D structure visualization and live parameter tuning:

::

    python tutorials/00_ni_synchrotron_benchmark/run_tutorial.py --gui
    python tutorials/01_ceo2_reduction_and_qdepend/run_tutorial.py --gui
    python tutorials/02_ceo2_nanoparticle_explicit_vs_analytical/run_tutorial.py --gui
    python tutorials/03_pto2_nanosheet_2d_pbc/run_tutorial.py --gui

For more detailed information and tutorials, please consult our `online documentation <https://Tominaka-Laboratory.github.io/orochi>`.

----------------------
Origins and Philosophy
----------------------

The creation of **Orochi** is rooted in a deep respect for the pioneering scientific foundations established over more than a century of X-ray physics and crystallography. In many ways, this work represents a deliberate re-examination and modern reconstruction of classical crystallographic principles, redesigned from the ground up to accelerate advanced materials discovery.

The author was first welcomed into the fascinating world of structural analysis through the inspiring guidance of **Prof. Anthony K. Cheetham** (University of Cambridge) around the 2012 centenary of Bragg's discovery of X-ray diffraction. Learning from foundational texts and software by **Prof. Simon J. L. Billinge** and other pioneers, the author set out to study over 100 years of scattering physics and computational crystallographic implementations. Crucially, this journey involved systematically testing and re-evaluating the physical approximations and simplifications that had historically been adopted out of necessity due to the computational limits of earlier eras—such as angle-independent form factor approximations, enforced 3D periodic boundary conditions requiring artificial vacuum supercells, and bulk volume density baselines.

A pivotal turning point occurred in 2024 through personal discussions with Prof. Simon J. L. Billinge, which illuminated the pathway toward open, modular Python packaging for modern scientific computing.

The Lessons of Dr. Fujio Izumi & Why We Chose GPLv3
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Early in this decade-long journey, the author had the privilege of receiving invaluable teachings and mentorship from the late **Dr. Fujio Izumi** (National Institute for Materials Science, NIMS), the legendary creator of *RIETAN* and co-creator of *VESTA*.

Dr. Izumi imparted two profound lessons that shaped the soul of Orochi:

1. **"Freely accessible, user-friendly, and physically rigorous tools are what truly propel scientific research forward."** (「フリーで使いやすいものが研究を推し進める」)
   Scientific progress flourishes when researchers—especially the rising generation—have unfettered access to transparent, high-fidelity computational engines without artificial barriers.

2. **The vulnerability of open academic software to corporate enclosure:**
   Dr. Izumi shared painful historical lessons from the early era of crystallographic computing, where academic software released without protective copyleft was appropriated by commercial corporations, wrapped into closed-source proprietary products, and effectively removed from the academic commons—at times jeopardizing continued development by independent researchers. To protect his work, Dr. Izumi chose strict copyright control and proprietary freeware agreements.

While honoring Dr. Izumi's protective intention, **Orochi adopts a different, forward-looking path: the GNU General Public License v3.0 (GPLv3)**.

By choosing **GPLv3 (strong copyleft)**, we achieve the best of both worlds:

* **100% Free and Transparent for Science:** Any researcher, student, or laboratory anywhere in the world can freely read, use, inspect, and modify the source code.
* **Permanent Legal Immunity Against Corporate Enclosure:** Under GPLv3, anyone who modifies or distributes software derived from Orochi *must* release their complete source code under the same GPLv3 license. No entity can ever take Orochi, enclose it behind a closed-source commercial paywall, or extinguish its open development.

Orochi is released as an enduring, shared asset for the global scientific community, ensuring that the **next generation of researchers can start from here with complete transparency, and continue building upon it for decades to come**.

-------
License
-------

Orochi and its official sub-packages are licensed under the **GNU General Public License v3.0 (GPLv3)**. See ``LICENSE.rst`` for the full license text.

------------------------
Academic Citation Policy
------------------------

Orochi is developed as an academic open-source project. If you use Orochi in scientific research leading to a publication, presentation, or thesis, please support its ongoing development by citing our publication:

.. code-block:: bibtex

    @article{tominaka2026orochi,
      title   = {Orochi: A Physics-Grounded Python Package for Pair Distribution Function Analysis of Crystalline and Low-Dimensional Materials},
      author  = {Tominaka, Satoshi},
      journal = {ChemRxiv},
      year    = {2026},
      url     = {https://chemrxiv.org/doc/d84591ff-85b9-489c-839a-4f7170dcc1c4}
    }

For citations of individual sub-packages (e.g., ``orochi.base``, ``orochi.pixia``, ``orochi.pdfget``), please refer to their respective repositories.

----------------------
Support and Contribute
----------------------

The Orochi project welcomes your expertise and enthusiasm!

If you see a bug or want to request a feature, please `report it as an issue <https://github.com/Tominaka-Laboratory/orochi/issues>`_ and/or `submit a fix as a PR <https://github.com/Tominaka-Laboratory/orochi/pulls>`_.

Feel free to fork the project and contribute. Improvements and fixes are always appreciated.

Before contributing, please read our `Code of Conduct <https://github.com/Tominaka-Laboratory/orochi/blob/main/CODE_OF_CONDUCT.rst>`_.

-------
Contact
-------

For more information on the Orochi framework, please visit the project `web-page <https://Tominaka-Laboratory.github.io/>`_ or email Dr. Satoshi Tominaka at tominaka.satoshi@nims.go.jp.