Problem at hand: Predict trip durations of taxis in New York City. 

<details>
<summary>Github lesson: Remove large files from previous commits</summary>
The solution is to use the bfg repo-cleaner package. Here is their [github repo] (https://github.com/rtyley/bfg-repo-cleaner)
and [official website] (https://rtyley.github.io/bfg-repo-cleaner/)
To download it (on Linux) either run the wget command: 
> 'wget -O bfg.jar https://repo1.maven.org/maven2/com/madgag/bfg/1.14.0/bfg-1.14.0.jar' 
or download it from their website. </br>
Inside the local repository directory run: 
> java -jar /path/to/bfg.jar 
Remove large files using
> 'java -jar path/to/bfg.jar --strip-blobs-bigger-than 100M' 
  'git reflog expire --expire=now --all'
  'git gc --prune=now --aggressive'		

If one of the big files is used by protected commits, it will STILL exist in your repository. In this case you need to manually delete it (using the rm command) and make a manual commit that removes it (git add file_to_be_removed and then git commit -m "removing big file") and then run the BFG on a fresh copy of the repo.



</details>
