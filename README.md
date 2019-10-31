# stable-matcher
The algorithm finds the stable matching for two parties with a set of preferences. The purpose of this project is to provide illustrative learning experience.

The Stable Matching algorithm used in this project is called the Gale-Shapley algorithm, which is a simple but powerful algorithm to find stable matches for two parties, each with a set of preferences. It was first introduced by D. Gale and L.S. Shapley in the article "College Admissions and the Stability of Marriage" published in 1962 in "The American Mathematical Monthly" (see http://www.jstor.org/stable/2312726). This algorithm and the theory behind it are so invaluable and interesting that it led Lloyd S. Shapley together with Alvin E. Roth to win the Nobel Prize in Economics in 2012 "for the theory of stable allocations and the practice of market design" (see http://www.nobelprize.org/nobel_prizes/economics/laureates/2012/).

# stable matching problem
The stable matching problem is given by 2 groups seeking relationship to another.
Both groups rank the other group by preference, such that each member of one group has a definite preference order of all the members of the other group.
The stable matching problem now requires a definite matching of both groups. Each member of one group is then connected to exactly one member of the other group.
If there exists a potential connection not included in a matching, in which both members prefer each other over their currently connected partners, then the matching is instable.
If no such potential connection exists, then the matching is stable.

## The algorithm:
```
S = a set of stable matching, M = group of males, W = group of females

S ⟸ { }
Initially all m ∈ M and w ∈ W have no partners
While ∃ m who is unmatched and has not proposed to every w
  w ⟸ first w on m's list to propose
    If w = unmatched
      Add m-w pair to S
    Else if w prefers m to her current parnter m'
      Delete m'-w pair from S
      Add m-w pair to S
    Else
      w rejects m
End While
Return S
```

## Our implementation
In our implementation, we have a female and a male group, each with a preference matrix of another.
The implementation then takes those 2 preference matrices, orders them, and applies the algorithm described above.
It then returns an array of fiances, which assigns each female their connected male, as determined in the matching returned by the algorithm.

## Setup mono
Follow the instructions here to install mono:
```
http://www.mono-project.com/docs/getting-started/install/linux/
```

Do not forget to install also these other packages:
```
sudo apt install mono-mcs
sudo apt install mono-devel
```

## How to compile and run
Compile:
```
mcs stableMatcher.cs utils.cs examples.cs
```
Run:
```
mono stableMatcher.exe
```

## Setup in Visual Studio (German version)

1. Start Visual Studio.
2. Go to the menu option "Datei->Neu->Projekt aus vorhandenem Code".
3. Choose "Visual C#" and click "Weiter".
4. You should see a dialog box "Wo sind die Daten?" Browse to the directory where you have clone the Git repository of the project and click on "Ordner auswählen".
5. Give a name to your visual studio program.
6. You should see a dialog box with the option "Ausgabetyp". Choose "Konsolenanwendung".
7. Click in "Fertigstellen".
8. Navigate to the file Program.cs generated by visual Studio and comment out the Main function and the program should now run.

Please just commit/push only those files that are needed to run the program in all platforms, i.e. please do not add/commit project files auto-generated by visual studio, for example: Program.cs and files with extensions .suo, .user, .sln, etc. Most of these files are already inside the .gitignore. But if you have more file-types or folders that are auto-generated or would otherwise bloat this repository please add them to the .gitignore file.
