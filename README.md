[![Open in Visual Studio Code](https://classroom.github.com/assets/open-in-vscode-2e0aaae1b6195c2367325f4f02e2d04e9abb55f0b24a779b69b11b9e10269abc.svg)](https://classroom.github.com/online_ide?assignment_repo_id=24110847&assignment_repo_type=AssignmentRepo)
# Day 10 Lab: Data Pipeline & Data Observability

**Student Email:** 2A202600786@vinuni.edu.vn
**Name:** Trần Mạnh Chánh Quân
**Student ID:** 2A202600786

---

## Mo ta

Bai lab xay dung mot **ETL Pipeline** tu dong (`solution.py`) de xu ly du lieu san pham:
- **Extract:** Doc du lieu tho tu `raw_data.json`.
- **Validate:** Loai bo cac record khong hop le (gia <= 0, category rong).
- **Transform:** Tinh gia giam 10% (`discounted_price`), chuan hoa `category` ve Title Case, va them cot timestamp `processed_at`.
- **Load:** Luu ket qua ra `processed_data.csv`.

Ngoai ra, bai lab con thuc hien **Stress Test** ve Data Observability: so sanh phan ung cua mot AI Agent (`agent_simulation.py`) khi dung du lieu sach va du lieu rac, ket qua duoc ghi trong `experiment_report.md`.

---

## Cach chay (How to Run)

### Prerequisites
```bash
pip install pandas
```

### Chay ETL Pipeline
```bash
python solution.py
```

### Chay Agent Simulation (Stress Test)
```bash
# 1. Chay pipeline de tao du lieu sach
python solution.py

# 2. Tao bo du lieu rac (poisoned data)
python generate_garbage.py

# 3. Chay Agent voi ca 2 bo du lieu de so sanh
python agent_simulation.py
```

---

## Cau truc thu muc

```
├── solution.py              # ETL Pipeline script
├── processed_data.csv       # Output cua pipeline
├── experiment_report.md     # Bao cao thi nghiem
└── README.md                # File nay
```

---

## Ket qua

- **Extract:** 5 records tu `raw_data.json`.
- **Validate:** 3 records hop le duoc giu lai, 2 records bi loai (1 gia am, 1 category rong).
- **Transform & Load:** 3 records duoc luu vao `processed_data.csv` voi cot `discounted_price`, `category` (Title Case) va `processed_at`.

**Stress Test:** Voi du lieu sach, Agent tra ve dung san pham (`Laptop`). Voi du lieu rac, Agent bi danh lua boi outlier va tra ve sai (`Nuclear Reactor $999999`). Ket luan: **Quality Data > Quality Prompt**. Chi tiet xem trong `experiment_report.md`.
