Problem at hand: Predict trip durations of taxis in New York City. 

<details>
<summary>Github lesson: Remove large files from previous commits</summary>
</br>
Problem: I accidentally committed a csv file of data whose size exceeds 100M which is the limit github allows. Next, I moved this file to .gitignore and made another commit. Pushing the changes did not work this time either because the big file is still in the repository history. The solution is to remove it from the previous commits. </br>

[1]: https://github.com/rtyley/bfg-repo-cleaner
[2]: https://rtyley.github.io/bfg-repo-cleaner/

The solution is to use the bfg repo-cleaner package. Here is their [github repo][1] and [official website][2]
</br> 

To download it (on Linux) either run the wget command: 
<code> wget -O bfg.jar https://repo1.maven.org/maven2/com/madgag/bfg/1.14.0/bfg-1.14.0.jar </code>
or download it from their website. </br>

Inside the local repository directory run <code> java -jar /path/to/bfg.jar </code> </br>

Remove large files using </br>
<code>java -jar path/to/bfg.jar --strip-blobs-bigger-than 100M </br>
  git reflog expire --expire=now --all   </br>
  git gc --prune=now --aggressive </code> </br>
  
If one of the big files is used by protected commits, it will STILL exist in your repository. In this case you need to manually delete it (using the rm command) and make a manual commit that removes it (git add file_to_be_removed and then git commit -m "removing big file") and then run the BFG on a fresh copy of the repo.



</details>
