# baolab

Important note: ISHAPE gives wrong results when compiled with gcc13 and the -O2 optimisation option (at least on MacOS). For now, possible workarounds are:  1) use older versions of gcc (gcc12 seems to work fine), 2) compile without the -O2 option enabled, 3) compile BAOlab with clang.
To test whether your version of bl works properly, run the test script cnvtst.bl:
bl < cnvtst.bl
This should produce an output image that looks like the image cnv_good.fits, and not like cnv_bad.fits.

From this page you can download my image processing/analysis program, BAOlab. This includes, among other things, the Ishape task for size measurements of compact sources (Larsen 1999, A&AS 139, 393) and the mksynth task for generation of synthetic images with realistic noise characteristics.

To get started, follow these steps:

Get the gzip'ed tar file and type 'tar xvzf baolab-x.y.z.tar.gz', where x.y.z is the version number.

Type 'make' in order to build BAOlab. You need gcc and the X11 libraries (R5 or later). You may have to edit the Makefile if your X11 libraries are not installed in /usr/X11 (for example, /usr/X11R6).

Type 'setenv BLPATH wherever baolab is located on your disk' - assuming you use a c-shell. For bash it would be 'export BLPATH=wherever baolab is located on your disk'. This makes it possible to access the parameter and help files also if you change to another directory. You may want to put this command in your .cshrc file (or .profile, .bashrc, .tcshrc, .login, or whatever) so you don't have to worry about it each time you want to run BAOlab.
  
Enter BAOlab by typing 'bl' - and have fun! There is a demo picture called 'demo.fts'. Type 'help baolab' for more information.

Things to be aware of:

A number of pre-defined compiler/linker options are defined in the Makefile. If BAOlab doesn't compile right away, try uncommenting another set of options. Pay particular attention if compiling on a Dec Alpha system (the -mieee compiler option must be set to avoid floating exceptions) or on some 64-bit Linux (and possibly other) systems where the X11 libraries are in a non-standard location.

Once the code has compiled, you can type 'make clean'. This will remove intermediate files produced during the compilation (*.o).

You may also be able to use one of pre-compiled binaries directly. Please note that these may not always be up-to date with the most recent version of the source code. You will probably have to make them executable with 'chmod +x bl-x.y.z' after downloading. Also note that, even if you get the pre-compiled binaries, you still need to get the tar file which contains the help file, sample baolab.par parameter file etc.
Diffusion kernels for WFPC2/F555W and ACS are included in the base directory:

  dk555.fits    - WFPC2 / F555W diffusion kernel (from WFPC2 handbook)
  
  dkernel.fits  - WFPC2 / F555W diffusion kernel (from TinyTim manual)
  
  dkaw4000.fits - ACS/WFC 4000A diffusion kernel (field center, ACS handbook)
  
  dkaw5500.fits - ACS/WFC 5500A diffusion kernel (field center, ACS handbook)
  
  dkaw8000.fits - ACS/WFC 8000A diffusion kernel (field center, ACS handbook)

BAOlab is still in the developing phase (and will probably remain there forever). However, as I am using it quite regularly myself one may hope that the most severe bugs have been worked out. No guarantees, though. Use it at your own risk. The features included in BAOlab are heavily biased towards applications that I have needed for my own work.

The recommended way to compile BAOlab is with gcc. Other compilers may work as well.

BAOlab does not have a sophisticated scripting language, but it does allow you to execute commands in a simple batch-mode.  More info can be found in the help file, baolab.hlp. To read about syntax, scripts etc. type 'help syntax' at the BAOlab prompt.

The code is pretty standard C code and should compile on most platforms. Over the years, I have successfully compiled and used BAOlab on Sun, Linux, SGI, HP, DEC alpha, Apple Powerbooks/Macbooks, and under Windows/Cygwin. However, I can't guarantee that any particular version of the code will compile or run on all of these platforms. It seems that gcc is becoming ever less forgiving and things sometimes tend to break when compiled with newer versions. I try to fix this when I become aware of it. 

Beware of the '.blrc' file - this file contains commands to be executed at start-up time and should be located in your BAOlab-home directory.

Finally, please drop me a note if you find BAOlab useful, or if you have any comments, questions or criticism.

BAOlab is named after Boserup Amateur Observatory (http://www.astro.ru.nl/~slarsen/bao/) - a small amateur observatory in Denmark where it all began.
