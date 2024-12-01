# paper_template

### Arxiv paper submission
1. Create submission directory
2. copy paper.tex, paper.bbl, and figures to submission/
3. (Optional) Delete unused figures
    - `cd submission`
    - List all used figures: `grep -roh '\\includegraphics\(\[.*\]\)\?{[^}]*}' *.tex | sed 's/.*{//;s/}//' > used_figures.txt`
    - List all files in the figures/ directory: `ls figures/ > all_figures.txt`
    - Sort files: `sort all_figures.txt -o all_figures.txt; sort used_figures.txt -o used_figures.txt`
    - `comm -23 all_figures.txt used_figures.txt > unused_figures.txt`
    - Review
    - Delete: `cat unused_figures.txt | xargs -I{} rm figures/{}`
    - `tar -czf paper_submission.tar.gz -C submission .`