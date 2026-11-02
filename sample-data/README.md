# VELOX test documents – fictional data

All companies, people, addresses, products, prices and numbers are invented.
Every file carries a "test document" note. The documents reproduce the **structure and traps**
of real supplier documents, so the workflow can be built and shown without any client data.

Customer: **VELOX Parts Distribution** (Austria / Czechia / Hungary branches).

| File | Supplier | Type | Format | Traps it tests |
|---|---|---|---|---|
| Auftragsbestätigung 250771204.PDF | LUBRIKA (AT) | OC | PDF, German, 3 pages | Quantity in boxes (Menge × Inhalt: 10 X 1 l, 4X4l, 3X5l); one line priced per litre (Bag in Box 20 l); delivery date per line; items split across pages |
| Lieferschein 402371188.PDF | LUBRIKA | DN | PDF, German | "1 Karton, 10 CU" – quantity as printed |
| doc00712420261015093312.pdf | LUBRIKA warehouse | DN | **Scan**, clean | No text layer; different layout; leading zero 0402370955; stamp |
| doc00712420261015093312_scan_slab.pdf | LUBRIKA warehouse | DN | **Scan**, poor | Same document, tilted, grey, noisy, stamp over the signatures |
| Detail objednávky č. 7710023456 PO4007703315.pdf | MAZOL (CZ) | OC | PDF, Czech | **Supplier name never printed**; PO only in the customer note; no positions; "0ks / 4ks" (delivered / ordered); prices with and without VAT, CZK with spaces |
| Dodací_list_26SV07311.pdf | MAZOL | DN | PDF, Czech, 2 pages | 24 lines, "ks" units, excise line |
| _26014420_921407_20261006_INV.xls + .pdf | FILTRONIQ (PL) | OC | Excel + PDF | Table starts at row 13; PO with " QWP" suffix; two product codes per line; two lines with a discounted price |
| UF_26009871_921407_20261014_SPC.XLS + .pdf | FILTRONIQ | DN | Excel + PDF, 14 pages | 395 lines, 12 pallets, **3 purchase orders in one DN**; 14 products split across two pallets; in the PDF the PO number wraps onto two lines |
| Template Order Conf.xlsx / Template Delivery Note.xlsx | – | – | Excel | Not supplier documents: must come out as "Unknown supplier" in Review.xlsx |
| Expected_result.xlsx | – | – | Excel | The correct answer for every document (73 OC rows, 425 DN rows) |

## Test scenarios

| Upload | Expected result |
|---|---|
| Everything | OC 73, DN 425; Review.xlsx: 2 templates, 2 skipped PDF duplicates, 4 scan lines |
| Only the Excel files | OC 46, DN 395; Review.xlsx: the 2 templates |
| Only the PDFs (all 8) | OC 73, DN 425 (the 14-page DN is read page by page); Review.xlsx: 4 scan lines |
