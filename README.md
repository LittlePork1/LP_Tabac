<img width="1280" height="640" alt="QB GoFast" src="https://github.com/user-attachments/assets/843536c3-0e7d-472b-966e-dde715092258" />


# 🌿 LP-TABAC

**LP-TABAC** is a complete **QBX Core** job script that allows players to harvest, process, and sell tobacco in an immersive way on your FiveM server.  

It uses **ox_target** and **ox_lib** for all interactions, and handles dynamic spawning/despawning of tobacco plants across predefined fields.

---

## 📌 Features

- 🌱 **Dynamic harvesting** – Random plant spawns within predefined fields  
- 🔄 **Automatic respawn** – Plants respawn once the field is fully harvested  
- 🏭 **Processing** – Convert harvested tobacco into cigarettes  
- 💰 **Selling** – Sell cigarettes to a ped or at a dedicated selling zone  
- 🔒 Harvest anti-spam using an `isHarvesting` flag  
- 🎯 Uses **ox_target** for all interactions  
- 📍 Configurable **processing**, **selling** zones, and **map blips**  
- 👷 **Job-restricted** interactions (only tobacco workers can see plants & zones)  

---

## 📂 Dependencies

Make sure you have installed:

- [qbx_core](https://github.com/Qbox-project/qbx_core)  
- [ox_target](https://github.com/overextended/ox_target)  
- [ox_lib](https://github.com/overextended/ox_lib)  

---

## ⚙️ Installation

1. Download the script and place it into your `resources/[qbx]` folder.  
2. Add the following to your `server.cfg`:  
    ```cfg
    ensure ox_lib
    ensure ox_target
    ensure qbx_core
    ensure LP-Tabac
    ```
3. Add the required **items** into your database (table `items`) or `shared/items.lua` depending on your inventory system.  

---

## 📦 Required Items

| name         | label         | weight | description                          |
|--------------|--------------|--------|--------------------------------------|
| tabac_brut   | Raw Tobacco   | 50     | Tobacco leaves for making cigarettes |
| cigarette    | Cigarettes    | 115    | Probably not good for you, but oh well |

**Add this to** your `ox_inventory/shared/items.lua` (or equivalent):

```lua
['tabac_brut'] = {
    label = 'Raw Tobacco',
    description = "Leaves used to create cigarettes",
    weight = 50,
    client = {
        image = "tabac_brut.png",
    },
},

['cigarette'] = { -- Social item that slightly reduces health
    label = 'Cigarettes',
    weight = 115,
    description = "These probably aren't good for you, but whatever",
    client = {
        anim = { dict = 'amb@world_human_aa_smoke@male@idle_a', clip = 'idle_c', flag = 49 },
        prop = { model = 'bzzz_cigarpack_cig002', 
        pos = vec3(0.0, 0.0, 0.0), rot = vec3(0.0, 0.0, 0.0), bone = 28422 },
        disable = { move = false, car = false, combat = true },
        usetime = 16000,
    }
},
 ```
## 📜 License
This project is licensed under the  GNU General Public License v3.0