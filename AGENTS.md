# Guidelines for AI Agents and Contributors

This document outlines the rules, directory structures, and contribution workflows for maintaining the `qinfoinfo` repository, particularly when adding or updating research laboratories and institutions.

---

## 1. Scope and Criteria

The main directory for research laboratories is located at:
- `content/lab/_index.md`

### Definition of Quantum Information Laboratories
A laboratory or research group is eligible for inclusion if its research aligns with the call for papers / topics of the **Quantum Information Technology Symposium (QIT)** in Japan, or broader quantum technology topics including:
- Quantum Computing (Theory, Algorithms, Software, Error Correction, Fault Tolerance)
- Quantum Communications, Quantum Cryptography, and Post-Quantum Cryptography (PQC)
- Quantum Measurement, Quantum Metrology, and Quantum Sensing
- Quantum Hardware & Devices (Superconducting, Trapped Ions, Neutral / Cold Atoms, Photonic, Semiconductor Spins, NV Centers, etc.)
- Quantum Information Theory, Foundations of Quantum Mechanics, and Open Quantum Systems
- Quantum Condensed Matter Theory (Topological Quantum Matter, Tensor Networks, etc.)
- Quantum-Classical Hybrid & Quantum HPC Integration

---

## 2. Organization and Ordering Rules

### 2.1 University & Institution Ordering: Geographically North to South
Universities and institutions must be ordered **geographically from North to South** across Japan:
1. **Hokkaido & Tohoku**: e.g., Hokkaido Univ. → Tohoku Univ.
2. **Kanto**: e.g., Univ. of Tsukuba → Univ. of Tokyo → Tokyo Tech (Science Tokyo) → UEC → TUAT → Tokyo Univ. of Science → Keio → Waseda → Chuo → YNU, etc.
3. **Chubu / Hokuriku / Tokai**: e.g., JAIST → Univ. of Toyama → Nagoya Univ.
4. **Kansai**: e.g., Kyoto Univ. → KIT → Ritsumeikan Univ. → Osaka Univ. → Kobe Univ.
5. **Chugoku & Shikoku**: e.g., Hiroshima Univ.
6. **Kyushu & Okinawa**: e.g., Kyushu Univ. → OIST
7. **Research Institutes & Centers**: e.g., RIKEN, AIST (G-QuAT), NII, NICT, QST
8. **Corporate / Industry Laboratories**: e.g., NTT, NEC, Toshiba, Fujitsu, Hitachi, IBM, Mercari R4D

### 2.2 Principal Investigator (PI) Ordering: Japanese Alphabetical Order (あいうえお順)
Within each university/institution, lab entries **must be sorted alphabetically by the PI's family name in Japanese kana order (あいうえお順)**, omitting honorifics (敬称略):
- Example: 井上 (Inoue, い) → 大岩 (Oiwa, お) → 北川 (Kitagawa, き) → 國廣 (Kunihiro, く) → 小泉 (Koizumi, こ) → 鹿野 (Shikano, し) → 鈴木 (Suzuki, す) → 高橋 (Takahashi, た) → 辻 (Tsuji, つ) → 富田 (Tomita, と) → 豊田 (Toyoda, と) → 根来 (Negoro, ね) → 初貝 (Hatsugai, は) → 藤原 (Fujiwara, ふ) → 御手洗 (Mitarai, み) → 山本 (Yamamoto, や)

---

## 3. Entry Format and Conventions

Each laboratory entry must follow this structure:

```markdown
### [Department / Division] [Laboratory Name] ([PI Full Name])
- 研究分野: [Research fields]
- HP: [URL or TBA]
```

### Conventions:
- **Heading level**: Always `###` for individual lab entries beneath the `## [University Name]` section.
- **PI Name**: Full name in parentheses, e.g., `(高橋 康博)`. Do not append titles such as `教授` or `先生`.
- **Department naming**: Avoid prefixing with `大学院` unless it is the standard or necessary distinction (e.g., prefer `情報科学研究科` or `システム情報系` over `大学院情報科学研究科`).
- **Research Fields (`研究分野`)**: List only quantum-related fields separated by middle dots (`・`) or commas, even if the lab also works on other unrelated topics.
- **Homepage (`HP`)**:
  - Always verify that the URL is public, accessible without login (e.g. avoid private Google Sites), and returns HTTP 200 (no broken redirects or 404s).
  - Prefer the official lab website or dedicated researcher page over general department directories.
  - If no official or personal website exists or is currently under preparation, specify `TBA`.

---

## 4. Git and Contribution Workflow

### 4.1 Never Push Directly to `main`
- **All updates must go through a Pull Request (PR)**. Do not push directly to the `main` branch.

### 4.2 Step-by-Step Procedure:
1. **Sync with latest `main`**:
   ```bash
   git checkout main
   git pull origin main
   ```
2. **Create a topic branch**:
   ```bash
   git checkout -b feature/add-[lab-name]-lab
   # or docs/..., fix/...
   ```
3. **Make edits and verify locally**:
   - Check URL validity.
   - Ensure alphabetical ordering within the university.
   - Run Hugo build to confirm there are no syntax or template errors:
     ```bash
     hugo --minify
     ```
4. **Commit with descriptive message**:
   ```bash
   git add content/lab/_index.md
   git commit -m "Add [PI Name] ([University Name]) to lab directory"
   ```
5. **Push branch and create PR**:
   ```bash
   git push -u origin feature/add-[lab-name]-lab
   gh pr create --base main --head feature/add-[lab-name]-lab --title "..." --body "..."
   ```
