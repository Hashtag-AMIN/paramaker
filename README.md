# Paramaker

[![Python](https://img.shields.io/static/v1?label=&labelColor=lightblue&message=Python&color=blue&style=flat&logo=python&logoColor=black)]()

### ***Paramaker is a Python tool designed to generate HTTP query strings based on a custom wordlist or vulnerable parameters used in web application security testing. It can take a list of custom parameters or use top vulnerable parameters and generate query strings with optional chunking for large wordlists, customizable keywords, and the flexibility to avoid unique query parameters.***

## Installation

### Clone the repository

```bash
git clone https://github.com/Hashtag-AMIN/paramaker.git
cd ./paramaker
chmod +x ./paramaker
./paramaker

# Global Access (Optional)

cp ./paramaker /usr/local/sbin/paramaker
paramaker
```

## Features

- **Customizable Wordlists:** Allows users to provide their own wordlist of parameters for generating query strings.
- **Predefined Vulnerable Parameters:** Includes predefined lists of parameters associated with common web vulnerabilities such as XSS, SQLi, LFI, RCE, etc.
- **Keyword Injection:** Option to specify a custom keyword (default is "hashtag") to be inserted into the query string.
- **Chunking Support:** Ability to split large wordlists into smaller chunks to prevent overwhelming the server or during large-scale testing.
- **Unique Parameters Option:** Option to prevent suffix numbers from being added to ensure parameters are not unique.


## Usage

### Basic Command Structure

```ruby

  └─# ./paramaker -h                          
                                                    
                                          _                 
                                          | |                
      ____  _____  ____ _____ ____  _____| |  _ _____  ____ 
      |  _ \(____ |/ ___|____ |    \(____ | |_/ ) ___ |/ ___)
      | |_| / ___ | |   / ___ | | | / ___ |  _ (| ____| |    
      |  __/\_____|_|   \_____|_|_|_\_____|_| \_)_____)_|    
      |_|                                                 
    
                                paramaker
                      https://github.com/Hashtag-AMIN/   
                      

  usage: paramaker [-h] [-w WORDLIST] [-k KEYWORD] [-c CHUNK] [-nu] [-all] [-xss] [-sqli] [-lfi] [-redir] [-rce]
                  [-ssrf] [-idor] [-ssti]

  Generate query strings from a wordlist with unique values and chunking and top parameters.

  options:
    -h --help         show this help message and exit
    -w --wordlist     Path to the wordlist (parameter file)
    -k --keyword      Keyword for generating unique values, default: 'hashtag'
    -c --chunk        Chunk size for splitting the wordlist, default: 20
    -nu --not-unique  Ignore to add suffix number for make unique parameter value
    -s --silent       Silent Mode
    -all --all        Add all Top Vulnerable Parameter
    -xss --xss        Add Top Vulnerable Parameter for XSS
    -sqli --sqli      Add Top Vulnerable Parameter for SQLI
    -lfi --lfi        Add Top Vulnerable Parameter for LFI
    -redir --redir    Add Top Vulnerable Parameter for Open Redirect
    -rce --rce        Add Top Vulnerable Parameter for RCE
    -ssrf --ssrf      Add Top Vulnerable Parameter for SSRF
    -idor --idor      Add Top Vulnerable Parameter for IDOR
    -ssti --ssti      Add Top Vulnerable Parameter for SSTI


```

### Example Usages

#### Generate Query Strings with Custom Wordlist

```bash
./paramaker -w /path/to/wordlist.txt
```

#### Generate Query Strings with XSS Vulnerable Parameters

```bash
./paramaker -xss 
```

#### Generate Query Strings with SQLi Vulnerable Parameters & Custom Wordlist

```bash
./paramaker -w /path/to/wordlist.txt -sqli
```

#### Generate Query Strings Using All Vulnerable Parameters & Custom keyword (default: 'hashtag'):

```bash
./paramaker -all -k "payload"
```

#### Generate Query Strings Without Adding Unique Suffix Numbers

```bash
./paramaker.py -w /path/to/wordlist.txt -nu -k "customvalue"
./paramaker.py -w /path/to/wordlist.txt --not-unique
```

### Generating Query Strings with Chunks

The tool can handle large wordlists by splitting them into smaller chunks. Use the `-c` option to specify the chunk size (default: 20):

```bash
./paramaker -w /path/to/wordlist.txt -c 15
```

### Generating Query Strings with Stdin data come

```bash
cat param.txt | ./paramaker -c 40
```

### Full Example of Using Multiple Vulnerability Flags

Generate query strings using parameters associated with XSS, SQLi, and LFI vulnerabilities and stdin, chunked into smaller parts and silent mode:

```bash
cat param.txt | ./paramaker -w /path/to/wordlist.txt -xss -sqli -lfi -k "attack-payload" -c 12 -nu -s
```

## Best usage

**Combine with other Tools:** Use Paramaker with tools like [waybackurls](https://github.com/tomnomnom/waybackurls) or [gau](https://github.com/lc/gau) with [unfurl](https://github.com/tomnomnom/unfurl) for optimal results in parameter fuzzing.

```bash
echo "site.com" | waybackurls | unfurl keys |  paramaker -s -c 12
gau "site.com" | unfurl keys |  paramaker -s -k "<test>" -nu
```

**Use Chunking for Large Wordlists:** Split large wordlists into manageable chunks to avoid server overload or block by WAFs.
```bash
paramaker -w /path/to/wordlist.txt -c 8
```

### Happy Hunting, Happy Learning ;) 🎯
