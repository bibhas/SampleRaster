The SampleRaster project implements a CUPS printer driver that simulates a
typical CMYK inkjet raster printer.  The driver provides the following
components:

    - CUPS raster filter (rastertosample)
    - CUPS command filter (commandtosample)
    - CUPS backend (sampletopdf)
    - Cocoa-based printer utility application (SampleUtility.app)
    - Cocoa-based print dialog plugin (SampleRasterPDE.bundle)
    - Printer icon
    - ICC color profiles
    - iPhoto/Preview printer presets
    - Custom printer-state-reason keywords
    - On-line help
    - Driver information file (sample.drv) which is compiled into a PPD file
      (sample.ppd).

The CUPS backend is provided for testing purposes only.  Most printer drivers
do not require their own backend - the system-supplied backends handle all
standard interfaces and network protocols for printing - and very few backends
are as complicated as the sampletopdf backend.


INSTALLATION

You must be running Mac OS X 10.6 or higher to compile or install from
source.  Packages created on Mac OS X 10.6.x and higher will also work on
10.4.x.

The "makepackage.sh" script can be used to create an installable driver
package, or you can just install from source directly with the following
command:

    xcodebuild -target SampleRaster install DSTROOT=/

Once you have installed the software, open the Print & Fax preference pane
and click on the "+" button to add a printer.  Choose the "Sample Raster Driver"
listing from the list and click "Add".


NOTES

The ink level monitoring supported by the printer utility and help will only
work with Mac OS X 10.5.3 and higher.  The driver as a whole works with Mac
OS X 10.4 and higher.

The backend writes the virtual printed pages to PDF files in a per-queue
directory in /Library/Caches, typically /Library/Caches/Sample_Raster_Driver
if the default printer name is used when you add the printer.

If you use this sample project as the start point for your product, 
before releasing your product, make sure you adjust the VALID_ARCHS value
of each target in the project file and the RC_ARCHS value to be passed to
'xcodebuild' in your build script, based on the versions of OS you support.