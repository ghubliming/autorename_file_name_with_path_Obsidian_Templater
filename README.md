
---

# Obsidian Templater Script: Auto-Rename Notes with Folder Path  

This Templater script automatically renames a newly created note by appending its folder path (relative to the vault) to its title. Since file names cannot contain slashes (`/`), the script replaces them with dashes (`-`).  

## 📌 Features  
- Extracts the note’s **relative folder path** within the vault.  
- **Replaces slashes (`/`) with dashes (`-`)** to ensure compatibility with file naming rules.  
- **Automatically renames the file** in the format:  
  ```
  OriginalTitle (Folder-Subfolder)
  ```

## 📜 Usage  
1. Install and enable the **Templater** plugin in Obsidian.  
2. Add the following script to your template:  

   ```javascript
   <%*
   const relativePath = tp.file.path(true); // Get full relative path
   const pathWithoutFilename = relativePath.substring(0, relativePath.lastIndexOf('/')); // Remove filename
   const folderPathSanitized = pathWithoutFilename.replace(/\//g, '-'); // Replace '/' with '-'
   const currentTitle = tp.file.title;
   const newTitle = `${currentTitle} (${folderPathSanitized})`;
   await tp.file.rename(newTitle);
   %>
   ```
3. Ensure Templater is set to **trigger on new file creation** in its settings.  
4. Create a new note, and the script will **automatically rename it** based on its folder path.  

## 🚀 Example  
### Folder Structure  
```
Vault/
 ├── Projects/
 │    ├── Research/
 │    │    ├── MyNote.md
```
### Before Running the Script  
- Note title: `MyNote`  

### After Running the Script  
- Note title: `MyNote (Projects-Research)`

## ⚠️ Notes  
- If the note is in the **root folder**, no folder name will be appended.  
- The script only renames the file **once**, when first created.  

---
