# GSOC21-SPF-String-Solvers
Documentation for GSOC 21 Project  

## Objectives:  

The overall objective is to improve string solver integration with SPF. This would be achieved by creating a template or example that could be followed when integrating solvers.

Since several solvers are already integrated, it was decided not to make breaking changes to the codebase that would require re-integration. Instead, a single method for integration would be identified, followed by integrating an existing solver as a template for future integrations.

## Timeline:  

##### 05/30 - 06/05  

Environment setup, builds of solvers and related libraries.
In examining the status of string solvers in SPF, it was found that z3str2 interface was broken. Solver ABC had an operational interface, but a difficult build process.

Decision was made with mentors to examine the way in which solver ABC was integrated and to perform the same type of integration with z3str3. This could then act as a template for further string solver integrations.

##### 06/06 - 06/12  

Detailed examination of ABC and z3str2 integration. z3str2 integration was via the executable through a running process, with both I/O redirection and file based input. ABC integration via C/C++ code native libraries and JNI. z3str3 has support for Java in a .jar file created during build process. The .jar file contains the JNI code to interface with the native libraries.

##### 06/13 - 06/26  

Examination of z3str3 input language and code development for translating the SPF global-graph and path condition to z3str3 inputs. z3str3 inputs limited to SMT-LIB string constructs, which will lead to limited Java string operation support in the implementation.

##### 06/27 - 07/03  

Initial integration of z3str3 into SPF via JNI operational. Still lacking ability to pass results back to SPF, and no support for z3str3 options in .jpf file. z3str3 exceptions with unknown string operations not handled. UNSAT results still throw exceptions.

##### 07/04 - 07/10  

Parsing results from z3str3 operational, passing results back to SPF operational. Support for z3str3 parameters inclusion in the .jpf file, Boolean string related options only.

##### 07/11 - 07/17  

z3str3 error handling improved, unknown string operation exceptions caught with warnings issued through SPF. Cleanup. Testing on string examples.

##### 07/18 - 07/24  

After discussion with mentors it was decided to add support for the BSU input solver. Integration of BSU input solver begun, integrated through included .jar files and single translation class.

##### 07/25 - 07/31  

BSU input solver working, passing values back to SPF. Testing on string examples.

##### 08/01 - 08/07  

Examination of benchmark performance begun, reproducing benchmark setups through Docker, initial examination of ABC performance on benchmarks to determine which failures were due to ABC and which might be attributed to JPF/SPF.

##### 08/08 - 08/14  



## Deliverables:  

Working z3str3 integration into SPF.
Working BSU input solver integration into SPF.   
Template for further string solver integrations.  

## Remaining Work:  

z3str3 support for Java string operation semantics is limited due to the input language based on SMT-LIB string theory constructs. This might be overcome using more complex translations of Java string operations into the language of the solver. It is possible that more solvers will use the SMT-LIB input specifications for uniformity,

Improvements to the BSU solver are underway, and a new version should be integrated into SPF when ready.
