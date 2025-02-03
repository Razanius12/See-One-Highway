# See One Highway

"See One Highway" is a fast-paced top-down 2D car racing game set in Japan, offering players an intense street-racing experience with simple gameplay and intuitive controls.

## Description  
This is a prototype game developed in **Construct 2**, currently in the alpha stage. The game lacks "quality of life" features, and most assets are placeholders. Debug mode may be accidentally triggered. Expect bugs during gameplay.

## Installation & Development Guide

### **Prerequisites**
1. **Construct 2** (to edit `.caproj` files).  
2. **NW.js** (Node-WebKit) for exporting and testing standalone builds.  
   - Download: [NW.js Builds](https://nwjs.io/) (use the "Normal" build to disable devtools).  

### **Exporting the Project**
1. **Export as `.caproj`**:  
   - Save your Construct 2 project as a `.caproj` file (project folder).  
2. **Export as NW.js Desktop**:  
   - In Construct 2, use **File > Export > NW.js (Windows/Mac/Linux)**.  
   - This generates a folder with `nw.exe` and `package.nw`.  

### **Optimizing Startup Time**  
The `package.nw` file bundles all assets and can slow startup. Here’s how to fix it:  

1. **Repackage `package.nw`**:  
   ```bash
   # Rename and extract the bundle
   cd path/to/exported/Win32-or-Win64-folder
   mv package.nw package.zip
   unzip package.zip -d package.nw
   rm package.zip  # Delete the original file
   ```  
   This reduces load times by avoiding ZIP compression overhead.  

### **Disable Chrome DevTools**  
Prevent users from accessing developer tools:  

1. Edit `package.json` in your exported folder:  
   ```json
   {
     "main": "index.html",
     "name": "SeeOneHighway",
     "chromium-args": "--disable-devtools --js-flags=--expose-gc"
   }  
   ```  
   - Add `--disable-devtools` to block `F12`/right-click access.  
   - Use the **"Normal" NW.js build** for full devtools removal.  

### **Fix Memory Bloat (Garbage Collection)**  
Force garbage collection to unload unused audio/textures:  

1. Add the following to `package.json`:  
   ```json
   "chromium-args": "--js-flags=--expose-gc"  
   ```  
2. Add this JavaScript code to your Construct 2 project (e.g., in a "Start of Layout" event):  
   ```javascript
   // Manually trigger garbage collection
   global.gc();  
   ```  

### **Font Handling**  
- All fonts are embedded as **sprite fonts** in Construct 2.  
- To edit fonts:  
  1. Rebuild the sprite font in Construct 2.  
  2. Avoid changing font names to prevent broken references.  

### **Full NW.js Guide**  
For advanced tweaks (e.g., window size, permissions), refer to:  
🔗 [Construct 2 NW.js Roundup Guide](https://www.construct.net/en/forum/construct-2/general-discussion-17/big-nw-js-roundup-news-tips-119428)  

### **Troubleshooting**  
- **Slow Startup**: Repackage `package.nw` as shown above.  
- **DevTools Still Accessible**: Use the **"Normal" NW.js build** instead of SDK.  
- **Memory Leaks**: Call `global.gc()` periodically in your code.  

## Credits

### **Development & Design**  
- **Razanius12**  
  Creator, Programmer, Composer, and Designer.  
  [GitHub Profile](https://github.com/Razanius12)  

### **Fonts**  
- **Bahnschrift**  
  Designed by Microsoft.  
  Source: [GitHub Repository](https://github.com/microsoft-fonts/Bahnschrift)  
  License: Bundled with Windows (free for non-commercial use).  

- **LCD Mono**  
  Designed by [Samuel Reynolds](https://www.dafont.com/lcd-lcd-mono.font).  
  License: 100% Free.  

- **VHS Gothic**  
  Designed by [Spottie Leonard](https://www.dafont.com/vhs-gothic.font).  
  License: 100% Free.  

### **Sound Effects (SFX)**  
**Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/):**  
- **Gas Station Ambience** by Npeo – [Source](https://freesound.org/s/207384/)  
- **Engine Start/Rev/Shutoff** by j_soundeffects – [Source](https://freesound.org/s/639227/)  
- **Car Horn (Volvo 240)** by j_soundeffects – [Source](https://freesound.org/s/636502/)  

**Licensed under [CC0 1.0 Universal](https://creativecommons.org/publicdomain/zero/1.0/):**  
- Text Blips (`malakme`) – [Pack](https://freesound.org/people/malakme/packs/26531/)  
- Collapse/Click SFX (`metalfortress`) – [Pack](https://freesound.org/people/metalfortress/packs/33727/)  
- Collision SFX (`qubodup`) – [Source 1](https://freesound.org/s/332058/), [Source 2](https://freesound.org/s/332056/)  
- Highway Noise (`Tetrisrocker`) – [Source](https://freesound.org/s/774489/)  
- Engine Idle (`mhad`) – [Source](https://freesound.org/s/390786/)  
- Nissan Rogue Idle (`itinerantmonk108`) – [Source](https://freesound.org/s/609825/)  

### **Music**  
- **EVDE** by 2ADVANCED – [Listen](https://on.soundcloud.com/MkaFJ5DbmNQZEF9T7)  
- **Ghosts on the Overpass (Remastered)** – Composed by Razanius12 – [Listen](https://on.soundcloud.com/hzx6R9xqH28ETZw76)  
- **bRAZCore** – Composed by Razanius12 – [BandLab](https://www.bandlab.com/songs/d2ec5377-63da-ef11-88f6-6045bd3473c0)  
- **InRazFies** – Composed by Razanius12 – [BandLab](https://www.bandlab.com/songs/5ff4974e-2cdb-ef11-88f6-6045bd3473c0)  
- **The Other Me** – Composed by Razanius12 – [BandLab](https://www.bandlab.com/songs/2c4ece89-e546-ec11-9820-e42aac7a5303)  

### **Special Thanks**  
- **Construct 2 Community** – For tools and inspiration.  
- **Sound Designers & Composers** – For openly shared assets.  
- **Playtesters & Supporters** – For feedback and enthusiasm.  
- **You** – For playing!  

### **License Notes**  
- All **SFX** are licensed under **CC BY 4.0** unless marked as **CC0 1.0 Universal** (public domain).  
- **Fonts** are used under their respective licenses (see attribution above).  
- **Music** by Razanius12 is provided under the creator’s terms.  

## Future Development  
The beta release will include core gameplay refinement. Full release timeline is TBD.  
