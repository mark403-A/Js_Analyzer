JS Analyzer

A lightweight client-side tool for extracting and analyzing JavaScript files to uncover security-relevant data.

Features
Extract endpoints, URLs, secrets, and credentials
Detect no-auth routes and exposed emails
Analyze both remote JS files and local uploads
Fast filtering and categorized results
Export findings (JSON / TXT)
Usage
Add a remote JS URL or upload local .js files
Click Analyze All
Review categorized results (endpoints, secrets, etc.)

1 : collect all js file (save js.txt)  
=======================================
2:  mkdir -p js_files
========================================
3. Run this |
             
cat js.txt | while read url; do
  filename=$(echo -n "$url" | md5sum | cut -d' ' -f1)

  curl -s --fail "$url" -o "js_files/$filename.js"

  if [ $? -eq 0 ]; then
    echo "[+] $url -> $filename.js"
  else
    echo "[-] Failed: $url"
  fi
done
====================================================
3: Upload js_files 
