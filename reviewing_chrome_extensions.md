# Reviewing Chrome Extensions

## Table of Contents

- [Initial Review](#initial-review)
  - [Example of Actual uBlock Origin](#example-of-actual-ublock-origin)
  - [Example Impersonating uBlock](#example-impersonating-ublock)
  - [Structure of Chrome Extension URL](#structure-of-chrome-extension-url)
- [Analysis Using CRX Viewer](#analysis-using-crx-viewer)
  - [Actual uBlock Origin Link for CRXViewer](#actual-ublock-origin-link-for-crxviewer)
  - [Entering Actual uBlock into CRXViewer](#entering-actual-ublock-into-crxviewer)
  - [Analysis of Benign Code Using CRXViewer](#analysis-of-benign-code-using-crxviewer)
- [Analysis of External References](#analysis-of-external-references)
  - [Tools for Reviewing Potentially Malicious Websites](#tools-for-reviewing-potentially-malicious-websites)
- [Additional Resources](#additional-resources)
  
## Initial Review

The first step in reviewing Chrome extensions is conducting a basic review of the source distributing the software before installation. This step, though seemingly obvious, is crucial in preventing users from falling victim to scams.

For example, a cursory review of a potentially malicious variant impersonating the well-known extension uBlock Origin (a popular ad-blocking extension) should raise suspicion. Discrepancies such as an inconsistent brand logo image, details not referencing the official developer, or lacking availability of the source-code can indicate a fake extension.

### Example of Actual uBlock Origin

```!
https://chromewebstore.google.com/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl
```

![Actual uBlock](https://hackmd.io/_uploads/HyTKSrbD0.png)   

### Example Impersonating uBlock

```!
https://chromewebstore.google.com/detail/ublock/epcnnfbjfcgphgdmggkamkmgojdagdnn
```

![Impersonating uBlock](https://hackmd.io/_uploads/BJpdff-v0.png)   


### Structure of Chrome Extension URL (actual uBlock link)

```!
https://chromewebstore.google.com/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl
```

| Portion                            | Description                                          |
| ---------------------------------- | ---------------------------------------------------- |
| `https://`                         | Protocol                                             |
| `chrome.google.com`                | Domain                                               |
| `/webstore/detail/`                | Path indicating access to the web store details page |
| `ublock-origin/`                   | Human-readable extension description                 |
| `cjpalhdlnbpafiamejdnhcphjbkeiagm` | Unique extension ID                                  |

## Analysis Using CRX Viewer

After a preliminary review, analyze the code within the extension. Google Chrome extensions are packaged into a CRX format. Various tools can open CRX files; in this guide, we use:

[CRXViewer by Rob Wu](https://robwu.nl/crxviewer/)   
[CRXViewer GitHub](https://github.com/Rob--W/crxviewer)

This tool allows for downloading, viewing, and analyzing CRX files. To use the tool, copy and paste the extension link you want to analyze. We'll start with the actual uBlock Origin extension to observe discrepancies between the genuine and impersonated versions.

### Actual uBlock Origin Link for CRXViewer

```!
https://chromewebstore.google.com/detail/ublock-origin/cjpalhdlnbpafiamejdnhcphjbkeiagm?hl
```

### Entering Actual uBlock into CRXViewer

![Entering uBlock Extension](https://hackmd.io/_uploads/rJ_YCkzwR.png)

### Analysis of Benign Code Using CRXViewer

![CRX Viewer](https://hackmd.io/_uploads/H1ZmZefDC.png)

## Analysis of External References

The final step is analyzing the potentially malicious sample's source-code. Look for external references such as API calls or IP addresses. Analyze these references using preferred tools:

#### Tools for Reviewing Potentially Malicious Websites:

- [Filescan.io](https://www.filescan.io/scan)
- [VirusTotal](https://www.virustotal.com/gui/home/upload)
- [Hybrid Analysis](https://www.hybrid-analysis.com/)
- [Urlscan.io](https://urlscan.io/)
- [UrlDNA](https://urldna.io/)
- [Recorded Future Tria.ge](https://tria.ge/)
- [AnyRun](https://any.run/)

### Additional Resources

- [Browser Extensions: How to Vet and Install Safely](https://security.berkeley.edu/education-awareness/browser-extensions-how-vet-and-install-safely)
- [CRXcavator by Duo](https://crxcavator.io/)
- [What are Extensions by Google](https://developer.chrome.com/docs/extensions/mv2/overview)
- [CRX Package Format](https://www.dre.vanderbilt.edu/~schmidt/android/android-4.0/external/chromium/chrome/common/extensions/docs/crx.html)
- [Security Tips for Developing CRX by Google](https://www.chromium.org/Home/chromium-security/education/security-tips-for-crx-and-apps/)
