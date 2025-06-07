# The Library of Babel: A Digital Interpretation



<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-gold.svg)](https://opensource.org/licenses/MIT)
[![Technology](https://img.shields.io/badge/Tech-HTML%20%7C%20CSS%20%7C%20JS-blueviolet.svg)](#-technology-stack)
[![Maintained](https://img.shields.io/badge/Maintained%3F-Yes-green.svg)](https://github.com/<YourUsername>/<YourRepoName>/commits/main)
[![Contribution](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)](#-contributing)

**Made by Abhinit Barua --- An interactive, infinite digital archive based on Jorge Luis Borges's timeless short story.**

[**► View Live Demo**](https://libraryofbabel-wheat.vercel.app/) <!-- Replace # with your live demo link -->
   •   
[**► Read the Documentation**](https://libraryofbabel-wheat.vercel.app/doc_page.html)

</div>

---

## 1. Project Philosophy

> "The universe (which others call the Library) is composed of an indefinite and perhaps infinite number of hexagonal galleries..."
>
> — Jorge Luis Borges

This project is not merely a website; it is an exploration of infinity, randomness, and order. It seeks to digitally manifest the core concepts of Borges's story by creating a seemingly infinite library that is paradoxically contained within a small, finite set of client-side code.

The core principle is **deterministic procedural generation**. Nothing is stored in a database. Every character on every page, every pattern on every book cover, and every "found" search result is generated on-the-fly from a unique, reproducible mathematical seed derived from its address. This creates a shared, persistent universe for all visitors without the need for a backend.

## 2. Features

*   **Infinite Browsing:** Navigate through a structurally infinite system of hexagons, walls, tables, shelves, and books.
*   **Procedural Generation:** Every book has a unique address, a unique cover with a "leather and foil" texture, and unique content.
*   **Deterministic Search:** Search for any string of text. The library will "find" your query by procedurally generating book locations where the text exists. The search is not exhaustive; it is creative.
*   **Interactive Reading:** A full-screen, immersive reader view with dynamic page sizing for optimal comfort.
*   **User Utilities:** Bookmark your favorite books (saved to Local Storage), copy direct links to specific books, and download books as PDFs.
*   **Advanced Documentation:** A comprehensive, interactive documentation page explaining the project's technical and philosophical underpinnings.
*   **Zero Dependencies:** Built entirely with vanilla HTML, CSS, and JavaScript. No frameworks, no build steps.

## 3. Technical Deep Dive: The Illusion of Infinity

The entire application rests on two computer science fundamentals:

#### A. Seeded Pseudo-Random Number Generators (PRNGs)

A standard `Math.random()` is non-deterministic. A **seeded PRNG**, however, will always produce the exact same sequence of "random" numbers if given the same starting number (the "seed"). This project uses the `mulberry32` algorithm for its speed and simplicity.

#### B. Hashing

A hashing function (`cyrb53` in this project) converts a string of any length (e.g., a book's address: `random-hex:4:8:2:77`) into a fixed-size integer. This integer becomes the unique seed for the PRNG.

#### The Generation Pipeline:

1.  **Address Creation**: A unique address string is formed for an object (e.g., a specific book or page).
2.  **Seeding**: The address string is hashed into a numerical seed.
3.  **Instantiation**: A PRNG is instantiated with this unique seed.
4.  **Generation**: The PRNG's deterministic "random" number sequence is used to generate everything:
    -   The total number of pages in a book.
    -   The characters on a specific page.
    -   The colors and filter parameters for an SVG book cover.
    -   The "location" of a search result.

This pipeline ensures that any request for the same address will always result in the exact same generated content, creating a persistent and shared universe.

## 4. Getting Started Locally

This project is fully client-side and requires no build process.

#### Prerequisites

*   A modern web browser that supports ES6 JavaScript.
*   A local web server for serving the files. Using a simple server avoids potential CORS issues with local file access (`file:///...`).

#### Installation & Running

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/AbhinitBarua/libraryofbabel.git
    cd <YourRepoName>
    ```

2.  **Start a local server.** If you have Python 3 installed, you can easily start one:
    ```bash
    python -m http.server
    ```
    If you have Node.js and `npx` available:
    ```bash
    npx serve
    ```

3.  **Open your browser** and navigate to `http://localhost:8000` (or the port specified by your server).

You can now browse the Library, the Documentation (`/documentation.html`), and explore the code.

## 5. Technology Stack

*   **HTML5:** Structured with modern, semantic tags (`<main>`, `<section>`, `<nav>`).
*   **CSS3:**
    *   Styled with CSS variables for easy theming.
    *   Uses Flexbox and Grid for robust, responsive layouts.
    *   Features advanced SVG filters (`<feTurbulence>`) for procedural texture generation.
*   **Vanilla JavaScript (ES6+):**
    *   No frameworks or external libraries (except `jsPDF` for PDF generation).
    *   State-driven architecture for predictable UI updates.
    *   Heavy use of procedural generation algorithms.
*   **jsPDF:** A third-party library included via CDN for client-side PDF generation.

## 6. Contributing

Contributions are welcome! Whether it's a bug fix, a performance improvement, or a new idea for procedural generation, feel free to open an issue or submit a pull request.

1.  **Fork** the repository.
2.  Create a new branch: `git checkout -b feature/YourAmazingFeature`.
3.  Make your changes and **commit** them with clear messages.
4.  **Push** to your branch: `git push origin feature/YourAmazingFeature`.
5.  Open a **Pull Request**.

Please ensure that any new features are documented and that the code adheres to the existing style and architecture.

## 7. License

This project is licensed under the MIT License. See the `LICENSE` file for details.
