# Huu Nguyen Phu — Engineering Portfolio

Source for [huuzng312.github.io](https://huuzng312.github.io), a multi-project portfolio focused on Design Verification and RTL Design.

## Information architecture

- The home page introduces Huu and presents an expandable gallery of project cards.
- Every project opens as a dedicated visual case study rather than expanding inside the home page.
- Detailed pages keep the story, architecture, media, evidence, and source links together.
- The current project shelf contains the RISC-V INT8 CNN Accelerator and the Autonomous Robot.

## Structure

```text
index.html                                # General portfolio home and project gallery
projects/riscv-cnn-accelerator/index.html # FPGA project detail page with video
projects/autonomous-robot/index.html      # Robotics project detail page
assets/css/portfolio.css                  # Shared responsive visual system
assets/js/portfolio.js                    # Theme and reveal interactions
assets/portfolio/                         # Project media
```

The site is plain HTML, CSS, and JavaScript and is served directly by GitHub Pages.
