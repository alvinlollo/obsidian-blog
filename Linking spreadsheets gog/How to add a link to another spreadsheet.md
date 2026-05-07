---
title: How to add a link to another spreadsheet
date: 2026-05-07
description: This shows how to make a hyprling in Google Docs to another spreadsheet in the same workbook.
author: Alvin Vilaythong
modified: 2026-05-07
tags:
  - Tutorials
  - Google
layout: docs
tagsobsidian://open?vault=Personal&file=1.%20Projects%2FBlog%2FHow%20to%20add%20a%20link%20to%20another%20spreadsheet:
---
{{< alert >}} This cannot be done on mobile as the link feature is not present. {{< /alert >}}
## Easy way
1. Select the cell you want to add a link with (Double click & CTRL + A)
2. Click the **Insert link** button in the top ribbon (CTRL + K) ![Workbook Select Menu](WorkBookSelectMenu.png)
3. After the link menu pops up click the **Sheets and named ranges** button. ![Hyperlink menu 1st page](LinkMenuHoverWorkbook.png)
4. After the menu changes select what workbook you would like to link. ![Hyperlink Menu 2nd page](LinkMenuWorkbook.png)

## Hard way
This way is suitable if you don't want to go back and forth

1. Open the workbook you would like to be the link **destination.** ![Workbook Select menu](WorkBookSelectMenu.png|496)
2. In the top address bar copy the workbook id e.g: ``#gid=XXXXXXXXXXXXX``. ![URL Bar with `#gid=828475600` selected](UrlBarGID.png)
3. Select the cell you want to add a link with (Double click & CTRL + A)
4. Click the **Insert link** button in the top ribbon (CTRL + K) ![Hyperlink button in the ribbon](LinkIcon.png)
5. After the link menu pops up paste the ``#gid=XXXXXXXXX`` into the link URL and apply it.
![`#gid=828475600` in the link menu](GID_in_url_popup.png)