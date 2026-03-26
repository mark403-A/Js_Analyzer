JS Analyzer

A lightweight client-side tool for extracting and analyzing JavaScript files to uncover security-relevant data.

Features
Extract endpoints, URLs, secrets, and credentials
Detect no-auth routes and exposed emails
Analyze both remote JS files and local uploads<img width="1128" height="450" alt="Screenshot 2026-03-26 130529" src="https://github.com/user-attachments/assets/03b37ed0-3b3c-4b4e-9228-bef3b31d4c25" />
<img width="1273" height="864" alt="Screenshot 2026-03-26 125055" src="https://github.com/user-attachments/assets/970a7d13-9762-40f3-91a4-2e188b4b9671" />

Fast filtering and categorized results
Export findings (JSON / TXT)
Usage
Add a remote JS URL or upload local .js files
Click Analyze All
Review categorized results (endpoints, secrets, etc.)

1 : collect all js file (save js.txt)  
2: step 
  mkdir -p js_files

cat js.txt | while read url; do
  filename=$(echo -n "$url" | md5sum | cut -d' ' -f1)

  curl -s --fail "$url" -o "js_files/$filename.js"

  if [ $? -eq 0 ]; then
    echo "[+] $url -> $filename.js"
  else
    echo "[-] Failed: $url"
  fi
done

3: Upload js_files 
