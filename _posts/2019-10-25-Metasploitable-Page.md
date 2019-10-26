---
title: Metasploitable
published: true
---
The following information shows the **Metasploitable walkthrough**

## [](#header-2)Introduction

   Metasploitable is a Linux based operating system that is designed in a vulnerable way so that the pen-testers and ethical hackers can test their skills. There is no security to the server hence it is always better to _run the metasploitable in a virtual environment_, as anyone can logon into it.
  
  ### [](#header-3)Requirements
  
   1. Download the vulnerable OS from the following link, **[metaploitable_download_link](https://sourceforge.net/projects/metasploitable/files/Metasploitable2/).**
   2. Kali Linux can be downloaded from the link, **[Kali_Linux_download_link](https://www.kali.org/).**
   3. Virtual Environment, here example is shown using VMware Workstation.
   4. Good understanding of Metasploit Framework(MSF).
   5. Linux commands usage.
       Install both the Operating Systems and run it.
      
      **_NOTE: Installation steps of Kali Linux can be found here,[Kali_linux_insatllation_guide](another_page)_.**
      
   When the OSes installed properly, one can encounter as shown in the following image,
   

   # [](#header-1) image 
   
   
   Login into the metasploitable terminal, Username and password would be given(commonly, it is msfadmin)
     
   Get the IP address, `# ifconfig`
   Use that IP_address and perform the following steps: 
        1. Scanning
        2. Vulnerability identification/Enumeration
        3. Exploitation and Access Gaining 

# [](#header-1) Network Penetration Testing

# [](#header-1)Step 1: Scanning 
   
   In this we need to find the ports that are open and also services running on that each port using which exploitation is done.

   * Open a terminal in Kali Linux and use **_namp_"** to perform the Network Scanning
   * Enter the following command, `# nmap -sS -Pn -n ip_address`
            - by default NMAP scans upto 1000 ports, to scan all the ports use either `-p`- or `-p 1-65535`
            - the above command offers the TCP SYN scan, to scan the UDP ports use `-sU`
            - the command also skips the host discovery(no Ping) and DNS resolution
            
      The results can be similar to the following image,
      
      # [](#header-1) image 
         
        ![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)



# [](#header-1)Step 1: Enumeration

nmap -Pn --script vuln 192.168.1.105

   BOOM!!!!!!!!

# [](#header-1)Step 1: Exploitation and Acess Gaining

There should be whitespace between paragraphs.

There should be whitespace between paragraphs. We recommend including a README, or a file with information about your project.

# [](#header-1)Header 1

This is a normal paragraph following a header. GitHub is a code hosting platform for version control and collaboration. It lets you and others work together on projects from anywhere.

## [](#header-2)Header 2

> This is a blockquote following a header.
>
> When something is important enough, you do it even if the odds are not in your favor.

### [](#header-3)Header 3

```js
// Javascript code with syntax highlighting.
var fun = function lang(l) {
  dateformat.i18n = require('./lang/' + l)
  return true;
}
```

```ruby
# Ruby code with syntax highlighting
GitHubPages::Dependencies.gems.each do |gem, version|
  s.add_dependency(gem, "= #{version}")
end
```

#### [](#header-4)Header 4

*   This is an unordered list following a header.
*   This is an unordered list following a header.
*   This is an unordered list following a header.

##### [](#header-5)Header 5

1.  This is an ordered list following a header.
2.  This is an ordered list following a header.
3.  This is an ordered list following a header.

###### [](#header-6)Header 6

| head1        | head two          | three |
|:-------------|:------------------|:------|
| ok           | good swedish fish | nice  |
| out of stock | good and plenty   | nice  |
| ok           | good `oreos`      | hmm   |
| ok           | good `zoute` drop | yumm  |

### There's a horizontal rule below this.

* * *

### Here is an unordered list:

*   Item foo
*   Item bar
*   Item baz
*   Item zip

### And an ordered list:

1.  Item one
1.  Item two
1.  Item three
1.  Item four

### And a nested list:

- level 1 item
  - level 2 item
  - level 2 item
    - level 3 item
    - level 3 item
- level 1 item
  - level 2 item
  - level 2 item
  - level 2 item
- level 1 item
  - level 2 item
  - level 2 item
- level 1 item

### Small image

![](https://assets-cdn.github.com/images/icons/emoji/octocat.png)

### Large image

![](https://guides.github.com/activities/hello-world/branching.png)


### Definition lists can be used with HTML syntax.

<dl>
<dt>Name</dt>
<dd>Godzilla</dd>
<dt>Born</dt>
<dd>1952</dd>
<dt>Birthplace</dt>
<dd>Japan</dd>
<dt>Color</dt>
<dd>Green</dd>
</dl>

```
Long, single-line code blocks should not wrap. They should horizontally scroll if they are too long. This line should be long enough to demonstrate this.
```

```
The final element.
```
