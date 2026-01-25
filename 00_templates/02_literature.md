---
created: <% tp.date.now("YYYY-MM-DD HH:mm:ss") %>
tags:
  - literature
source:
---

<%*
const CONFIG = {
  BASE_FOLDER: "01_data",
  // フォルダ階層用
  FOLDER_DATE_FORMAT: "YYYY/MM/DD",
  // ファイル名に付与する日付フォーマット
  FILE_DATE_FORMAT: "YYYY-MM-DD",
  // 任意のタイトルを設定, 空欄("")の場合はデフォルトのファイル名を使用
  TITLE: "",
  // 日付表示位置："NONE" (なし), "PREFIX" (前方), "SUFFIX" (後方)
  DATE_POSITION: "PREFIX"
}

const createFolderIfNotExists = async (path) => {
  try {
    await app.vault.createFolder(path)
  } catch {
    // フォルダが既に存在
  }
}

const getUniqueName = async (folder, base) => {
  let name = base
  let i = 1
  while (app.vault.getAbstractFileByPath(`${folder}/${name}.md`)) {
    name = `${base}_${i++}`
  }
  return name
}

const moveFileToFolder = async (fileTitle, folder) => {
  await createFolderIfNotExists(folder)
  const uniqueName = await getUniqueName(folder, fileTitle)
  await tp.file.move(`${folder}/${uniqueName}`)
  return uniqueName
}

const notifyIfRenamed = (original, newName) => {
  if (original !== newName) {
    new Notice(`ファイル名重複のため "${newName}" に変更されました`);
  }
}

const generateFileName = (title, position, dateFormat) => {
  const baseTitle = title?.trim();
  if (!baseTitle) {
    return tp.file.title;
  }
  const dateStr = tp.date.now(dateFormat);

  switch (position) {
    case "PREFIX": return `${dateStr}_${baseTitle}`;
    case "SUFFIX": return `${baseTitle}_${dateStr}`;
    case "NONE":   return baseTitle;
    default:       return baseTitle;
  }
}

try {
  const folderPath = `${CONFIG.BASE_FOLDER}/${tp.date.now(CONFIG.FOLDER_DATE_FORMAT)}`;
  const newFileName = generateFileName(CONFIG.TITLE, CONFIG.DATE_POSITION, CONFIG.FILE_DATE_FORMAT);
  const finalName = await moveFileToFolder(newFileName, folderPath);
  notifyIfRenamed(newFileName, finalName);
} catch (error) {
  new Notice(`エラー: ${error.message}`);
}
%>
