# Flask Lab Docker CI/CD Project

This repository contains a **CI/CD pipeline** for building, scanning, and optionally pushing a Docker image of a Flask application using **Jenkins** and **Trivy**.

---

## Overview

The pipeline automates the following tasks:

1. **Docker Build**  
   - Builds a Docker image from the Flask app located in `flask-hello-lab/`.  
   - Image is tagged as `flask-lab-training:latest`.

2. **Security Scan (Trivy)**  
   - Scans the Docker image for `HIGH` and `CRITICAL` vulnerabilities.  
   - Generates a report in `trivy-report.txt`.  
   - The build does **not fail** on vulnerabilities, allowing review of the report.

3. **Push to Private Registry**  
   - If the build succeeds, the image is tagged for a private Docker registry (`172.31.29.60:5000`) and pushed.  

4. **Post Actions**  
   - Archives the `trivy-report.txt` artifact.  
   - Logs a warning if the image is not secure.

---
