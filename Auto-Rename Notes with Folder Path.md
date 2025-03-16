<%*
const relativePath = tp.file.path(true); // e.g. "Folder/Subfolder/NoteTitle.md"
const pathWithoutFilename = relativePath.substring(0, relativePath.lastIndexOf('/')); // e.g. "Folder/Subfolder"
const folderPathSanitized = pathWithoutFilename.replace(/\//g, '-'); // changes "Folder/Subfolder" to "Folder-Subfolder"
const currentTitle = tp.file.title;
const newTitle = `${currentTitle} (${folderPathSanitized})`;
await tp.file.rename(newTitle);
%>
