.. include:: ../../macros.rst



.. _general_information_releases:

========
Releases
========

The following table describes the different versions of |foxbms| that were released.
The first line is the most recent one, the last one the oldest one.

+---------------+----------------------+----------------------------------------------------------------+------------+
| Documentation | Embedded Software    |                          |foxbms| Hardware                     | |foxConda| |
+               +----------+-----------+--------------+-----------------+-------------+-----------------+            +
|               | Primary  | Secondary | |BMS-Master| | |BMS-Interface| | |BMS-Slave| | |BMS-Extension| |            |
+===============+==========+===========+==============+=================+=============+=================+============+
| 0.5.0         | 0.5.0    | 0.5.0     | 1.0.2        | 1.0.1           | 1.0.1       | 1.0.2           | 0.5.0      |
+---------------+----------+-----------+--------------+-----------------+-------------+-----------------+------------+
| 0.4.4         | 0.4.4    | 0.4.4     | 1.0.1        | 1.0.1           | 1.0.1       | 1.0.1           | 0.4.3      |
+---------------+----------+-----------+--------------+-----------------+-------------+-----------------+------------+
| 0.4.3         | 0.4.3    | 0.4.3     | 1.0.0        | 1.0.0           | 1.0.0       | 1.0.0           | 0.4.3      |
+---------------+----------+-----------+--------------+-----------------+-------------+-----------------+------------+
| 0.4.2         | 0.4.2    | 0.4.2     | 1.0.0        | 1.0.0           | 1.0.0       | 1.0.0           | 0.4.0      |
+---------------+----------+-----------+--------------+-----------------+-------------+-----------------+------------+
| 0.4.1         | 0.4.1    | 0.4.1     | 1.0.0        | 1.0.0           | 1.0.0       | 1.0.0           | 0.4.0      |
+---------------+----------+-----------+--------------+-----------------+-------------+-----------------+------------+
| 0.4.0         | 0.4.0    | 0.4.0     | 1.0.0        | 1.0.0           | 1.0.0       | 1.0.0           | 0.4.0      |
+---------------+----------+-----------+--------------+-----------------+-------------+-----------------+------------+

The following section summarizes the release notes for the different versions of the documentation.

Release 0.5.0
-------------

A new project structure is now used by foxBMS. The documentation is no more contained in the embedded software sources and has its own repository. FreeRTOS and hal have their own repository, too.
A central repository called foxBMS-setup is now used. It contains several scripts:

    - bootsrap.py gets all the repositories needed to work with foxBMS
    - build.py is used to compile binaries and to generate the documentation
    - clean.py is used to removed the generated binaries and documentation

Release notes:
	
    - New project structure
    - Embedded Software
	
        - Added support for external (SPI) EEPROM on the BMS-Master
        - Redesign of can and cansignal module to simplify the usage
        - Added support for triggered and cyclic current measurement of Isabellenhuette current sensor (IVT)
        - Current sensor now functions by default in non-triggered modus (no reprogramming needed for the sensor)
	
    - Sphinx Documentation:
	
        - Updated and restructured complete documentation
        - Restructured file and folder structure for the documentation
        - Added safety and risk analysis section
        - Cleaning up of non-used files in the documentation
        - Consistency check and correction of the naming and wording used
        - Addition of the source files (e.g., Microsoft Visio diagrams) used to generate the figures in the documentation
        - Reformatted the licenses text formatting (no changes in the licenses content)
        - Updated the battery junction box (BJB) section with up-to-date components and parameters

Release 0.4.4
-------------

Release notes:

	- Full update and correction of the documentation based on the feedback received
	- Consistency check and update of the wording and naming used in the hardware, software and documentation
	- Improved checksum process
	
		- faster implementation of checksum script
		- checksum script is called automatically after "python tools/waf-1.8.12 configure build"
		- build command "python tools/waf-1.8.12 configure build chksum" NO longer supported

Release 0.4.3
-------------

Starting from this version, a checksum mechanism was implemented in |foxbms|. If the checksum is active and it is not computed correctly, it will prevent the flashed program from running. Details on deactivating the checksum can be found in the :ref:`software_documentation_faq`, in :ref:`faq_checksum`.

Release notes:

    - Important: Changed contactor configuration order in the software to match the labels on the front
    
        - Contactor 0: CONT_PLUS_MAIN
        - Contactor 1: CONT_PLUS_PRECHARGE
        - Contactor 2: CONT_MINUS_MAIN
        
    - Fixed an bug which could cause an unintended closing of the contactors after recovering from error mode
    - Increased stack size for the engine tasks to avoid stack overflow in some special conditions
    - Added a note in the documentation to indicate the necessity to send a periodic CAN message to the BMS
    - Fixed DLC of CAN message for the current sensor measurement
    - Added checksum verification for the flashed binaries
    - Updated linker script to allow integration of the checksum tool
    - Activated debug without JTAG interface via USB

Release 0.4.2
-------------

Release notes:

    - Removed schematic files from documentation, registration needed to obtain the files
    - Added entries to the software FAQ



Release 0.4.1
-------------

Release notes:

    - Corrected daisy chain connector pinout in quickstart guide
    - Corrected code  for contactors, to allow using contactors without feedback
    - Corrected LTC code for reading balancing feedback
    - Quickstart restructured, with mention of the necessity to generate the HTML documentation

Release 0.4.0
-------------

Beta version of |foxbms| that was supplied to selected partners for evaluation.