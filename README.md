

### Project Details

#### 1. Data Input
- **OCR Input**: Simulated medical bills with fields like patient name, ICD-10 code, MDC code, charge, and procedure.
- **EDI Input**: HIPAA 837 claim messages with claim ID, charge, and ICD-10 code.
- **MDC Mapping**: Simplified dictionary mapping ICD-10 codes to MDC codes (e.g., E11.9 → MDC 10). In practice, use a full CMS MDC-DRG table.

#### 2. OCR Processing
- **Function**: `extract_structured_data_ocr`
- **Method**: Regex to extract fields (patient, ICD-10, MDC, charge, procedure).
- **Challenges**: OCR errors (e.g., misread numbers). Mitigated with robust regex patterns.
- **Real-World**: Replace sample `ocr_texts` with Tesseract output:
  ```python
  image = Image.open('medical_bill.png')
  text = pytesseract.image_to_string(image)

  ```
Copyright (c) 2025 John Ryan - 10 May 2025

All rights reserved.

This software may not be copied, modified, distributed, or used in any way without express written permission from the author.
