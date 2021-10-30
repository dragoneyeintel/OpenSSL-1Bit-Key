# OpenSSL-1Bit-Key
Modified OpenSSL binary allowing for smaller RSA key generation (1 Bit or Larger). To run the precompiled binary, simply execute the \bin\openssl.exe executable.

E.G. `openssl.exe genrsa -out key.pem 255`

## Modifications Made
The openssl-1.1.1f\crypto\rsa\rsa_local.h folder:
Replaced minimum bit value of 512 to 1.


The openssl-1.1.1f\test\recipes\15-test_genrsa.t folder:
Coppied `15-test_ecpram.t` into `15-test_genrsa.t` to avoid halts during `nmake test`. 
This will create a warning but will allow for checking of all of the other tests.


## Build
Before building ensure NASM and Pearl are installed and in the System PATH. If you do not have Perl already, I suggest installing [ActiveState Perl](https://www.activestate.com/products/perl/).
Open the ActiveState Perl Command Prompt.
Open the Visual Studio Command Prompt within this prompt:

`C:\Program Files (x86)\Microsoft Visual Studio\2019\BuildTools\VC\Auxiliary\Build\vcvars64.bat`


Configure: `perl Configure VC-WIN64A`

Make: `nmake` `nmake test` `nmake install`

May have to point the OpenSSL configuration variable to the included .cnf file:
`set OPENSSL_CONF=C:openssl.cnf`
