# 🧟 Survival Gear Selection

A Python-based inventory management system for a survival game.  
It allows players to buy and manage essential items while balancing **weight and money** limits.

## 📌 Features
👉 **Survival Store** - Players can buy weapons, medical kits, and survival gear  
👉 **Auto-Select Best Items** - Optimized selection for combat, utility, and survival  
👉 **Custom Inventory Management** - Players can manually pick items and track weight  
👉 **Fully Text-Based** - Works in **Google Colab** and **Local Python** environments  

## 🚀 How to Run (Google Colab)
1. Open [Google Colab](https://colab.research.google.com/)
2. Copy and paste the code from `Survival_Gear_Selection.ipynb`
3. Run the script to display store items and auto-select the best inventory

## 💻 How to Run Locally
1. Clone the repo:
   ```bash
   git clone https://github.com/YOUR_GITHUB_USERNAME/Survival-Gear-Selection.git
   cd Survival-Gear-Selection
   ```
2. Install pandas (if not installed):
   ```bash
   pip install pandas
   ```
3. Run the Jupyter Notebook:
   ```bash
   jupyter notebook Survival_Gear_Selection.ipynb
   ```

## 🌟 Example Output
```mathematica
==== Survival Store ====
        name  weight  cost  useful
 Baseball Bat     2.0   150    True
 Rusty Machete     1.5   200    True
 Handgun + 6 Bullets     3.0   500    True
 Backpack [Increases Carry Limit]     1.0   100    True
 First Aid Kit     2.0   250    True

==== Selected Inventory ====
- Rusty Machete (1.5kg) - 200 💎
- Handgun + 6 Bullets (3kg) - 500 💎
- Backpack (1kg) - 100 💎
- First Aid Kit (2kg) - 250 💎

Total weight: 7.5/15kg
Remaining money: 50 💎
```

## 🛠️ Future Features
- Add randomized inventory each time
- Implement player skill stats affecting item usage
- Introduce difficulty modes with limited supplies

## 🐟 License
This project is open-source and available under the MIT License.

---

### **📄 Folder Structure (For GitHub Repo)**
```
📂 Survival-Gear-Selection/
 ├── 📄 `README.md` (Project Documentation)
 ├── 🐍 `Survival_Gear_Selection.ipynb` (The main Jupyter Notebook script)
 ├── 📂 `data/` (Optional: Store external item lists)
 ├── 📜 `.gitignore` (To exclude unnecessary files)
```

---

### **📝 Extra: Make It Interactive in Google Colab**
If you want **manual selection instead of auto-picking**, replace this part:
```python
selected_items = [
    {"name": "Rusty Machete", "weight": 1.5, "cost": 200},
    {"name": "Handgun + 6 Bullets", "weight": 3, "cost": 500},
    {"name": "Backpack", "weight": 1, "cost": 100},
    {"name": "First Aid Kit", "weight": 2, "cost": 250},
]
```
With:
```python
selected_items = []
total_weight = 0
remaining_money = 900

while True:
    print("\nYour Current Inventory:")
    for item in selected_items:
        print(f"- {item['name']} ({item['weight']}kg) - {item['cost']} 💎")
    print(f"Total Weight: {total_weight}/15kg | Remaining Money: {remaining_money} 💎")

    item_name = input("\nEnter item name to buy (or type 'done' to finish): ").strip()
    if item_name.lower() == 'done':
        break
    
    found_item = next((item for item in items if item["name"].lower() == item_name.lower()), None)
    
    if found_item:
        if total_weight + found_item["weight"] <= 15 and remaining_money - found_item["cost"] >= 0:
            selected_items.append(found_item)
            total_weight += found_item["weight"]
            remaining_money -= found_item["cost"]
            print(f"✅ Added {found_item['name']} to your inventory!")
        else:
            print("⚠️ Not enough money or carrying capacity!")
    else:
        print("❌ Invalid item name! Please try again.")
```
This will allow manual item selection in Google Colab.


