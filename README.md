[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24112718&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** lexuantiendat30012004@gmail.com
**Student ID:** 2A202600549
**Name:** Lê Xuân Tiến Đạt

---

## Mo ta

Bai lab nay xay dung mot **ETL Pipeline** tu dong (Extract - Validate - Transform - Load)
de lam sach du lieu san pham, ket hop voi **Data Observability** (logging + timestamp).
Sau do chay thi nghiem **Stress Test** cho mot AI Agent tren hai bo du lieu (sach va rac)
de chung minh tam quan trong cua chat luong du lieu.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas pytest
```

### 1. Chay ETL Pipeline
```bash
python solution.py
```
Pipeline se doc `raw_data.json`, loai bo cac record khong hop le (gia <= 0, category rong),
tinh `discounted_price` (giam 10%), chuan hoa category ve Title Case, them cot `processed_at`,
va luu ket qua ra `processed_data.csv`.

### 2. Tao du lieu rac (Garbage Data)
```bash
python generate_garbage.py
```

### 3. Chay Agent Simulation (Stress Test)
```bash
python agent_simulation.py
```
Lenh nay so sanh cau tra loi cua Agent khi dung du lieu sach va du lieu rac.

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── raw_data.json            # Du lieu dau vao
├── processed_data.csv       # Output cua pipeline
├── generate_garbage.py      # Tao garbage_data.csv
├── agent_simulation.py      # Stress test cho AI Agent
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Pipeline:** Xu ly 5 records dau vao, giu lai **3 records** hop le, loai bo **2 records**
  (id=3 gia <= 0, id=4 category rong).
- **Stress Test:**
  - Clean Data -> Agent tra loi dung: *Laptop at $1200*.
  - Garbage Data -> Agent tra loi sai: *Nuclear Reactor at $999999* (bi danh lua boi outlier).
- **Ket luan:** Quality Data > Quality Prompt. Du lieu sach la nen mong cho AI dang tin cay.
