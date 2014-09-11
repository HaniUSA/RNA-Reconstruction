                                                             ReadMe 
                                                     RNA_Reconstructing_from_Fragments


Introduction:
------------ there are two programs included within;
             1- the main program : RNA_RECONST_GRAPH.cpp     That is the main program, that will reassemble the RNA strand(s) from its G, UC splicing enzymes fragments.
             2- xtra_Dev_Debug_Version.cpp                   That version is for development and debugging, it shows every step results, so we are able to reassure the logic used 
			                                                 

Compiling: Both programs are writing in C++ language, to compile any of them on eniac, simply use the traditional method 
---------        ie;  g++ RNA_RECONST_GRAPH.cpp -o run
                ./run		   
		   Note: If you are using Windows machine, please go to line 345 and uncomment the system("pause")		
				
Program's Goal: the goal of the program is to reconstruct RNA strand - or all possible strands - from  giving fragments that results from using splicing enzymes G and UC 
--------------- on two identical RNA strands. 
			 
			 
Description:
----------- The RNA strands is consists of four bases U,A,C,G. In Biology, there are some splicing enzymes that can be used to splice RNA strands at specific regions.
            for example G-enzyme, if used on RNA strand, it will splice the RNA strand right after each G base is found. Similarly, UC-enzyme will splice the RNA enzyme 
			right after any U or C base  is found. Because we can have two identical copies of RNA strands, we can use G-enzyme on one of them, and UC-enzyme on the 
			second strand, the result will be fragments that  ends on G bases, U bases or C bases or A bases. But because we know which fragments resulted from which 
			enzyme treatment, we can determine the last base on the RNA easily.
            **The fragments resulting from treating the first RNA strand by G-enzyme will be:
             1- either ending on G base
             2- or ending on non-G base , that will be the last fragment.
            **The fragments resulting from treating the first RNA strand by UC-enzyme will be:
             1- either ending on U or C base 
             2- or ending on non U or C base, that will be the last fragment.
The Logic:
---------  because the RNA strands consists of four bases, G,C,A,U, it must be ending with one- and only one - of those.
           1- If it ends with G      -----> then the abnormal fragment will show up on the UC-enzyme treatment as a fragment that ends with G.
           2- If it ends with C or U ----->	then the abnormal fragment will show up on the G-enzyme treatment as a fragment that ends with C or U.
           3- If it ends with A      -----> then the abnormal fragment will show up on both G-enzyme treatment and UC_enzyme treatment.	   
		   Therefore, after the first enzyme treatment, we can easily conclude the last fragment .
		   To determine the first fragment: if we imaging treating fragments that resulted from treating RNA with G_enzyme with UC_splicing enzyme and fragments 
		   that resulted from  treating the copy of RNA with UC_splicing enzyme with the G_enzyme; then group the inner bases into one vector and the extended- outer
		   bases- into another, by taking the intersects of these two vectors out, we end up with only two base( the ends ), because we know the last fragment
		  then we can conclude the first fragment.
		   Then the problem becomes finding Eulerian paths( circuits) that starts on the first fragment, and ends at the last fragment, and it must pass by all vertices 
		   ( the external bases)through the edges ( inner bases).	Then Eulerian paths resemble the possible RNA structures.	
		  
Known Bugs:
---------- None, please let me know if you find any at      
           Hani Aboudeshisha               hani.csci@gmail,com

		  
		  
		  