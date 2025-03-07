---
title: "History"
url: /refguide/history-dialog/
weight: 50
tags: ["studio pro", "commit", "history", "select revision", "commit history"]
---
## 1 Introduction

Use the **History** dialog box to look at all the changes that have been committed to a development line of an app. You can open this dialog box from the **Version Control** > **History…** menu item. This dialog box is also used when selecting a revision to merge from, create a branch line off, or to create a deployment archive from.

## 2 Revisions

{{< figure src="/attachments/refguide/modeling/menus/version-control-menu/history-dialog/revisions.png" alt="Revisions Image" >}}

Each line in the grid represents a revision in the repository. For each revision the following information is shown, more information about each of these values is available below:

* [Revision](#revision)
* [Changes](#changes)
* [Author](#author)
* [Date](#date)
* [Time](#time)
* [Message](#message)

By selecting a revision in this grid, the tabs below the grid will be filled with information about this revision.

### 2.1 Revision{#revision}

A unique alphanumeric identifier of the revision in the repository. The revision identifier is the Git hash for the commit and is unique for a whole repository.

### 2.2 Changes{#changes}

A visual summary of the changes in the selected revision, each icon represents different type of change:

| Icon | Change Type | Notes |
| --- | --- | --- |
| {{< figure src="/attachments/refguide/modeling/menus/version-control-menu/history-dialog/MergeRevision.png" width=32 alt="Merge commit icon" >}} | Merge commit | Indicates that the commit is a merge of two different commits.<br/>Hovering over will show both the parent [revisions](#revision). |
| {{< figure src="/attachments/refguide/modeling/menus/version-control-menu/history-dialog/RevChangesModel.png" width=32 alt="Model changes icon" >}} | Model changes | Indicates that there were some changes made to the app model.<br/>For example, changes to the domain model, microflows, or pages. |
| {{< figure src="/attachments/refguide/modeling/menus/version-control-menu/history-dialog/RevChangesDisk.png" width=32 alt="Changes on disk icon" >}} | Changes on disk | Indicates that there were changes on disk.<br/>For example, a file was added or removed. |
| {{< figure src="/attachments/refguide/modeling/menus/version-control-menu/history-dialog/RevChangesVersion.png" width=32 alt="Studio Pro changes icon" >}} | Studio Pro changes | Indicates that there was a change to the Studio Pro version used to work with the app.<br/>For example, when upgrading the app from a previous version to the latest one. |
| {{< figure src="/attachments/refguide/modeling/menus/version-control-menu/history-dialog/Solution.png" width=32 alt="Solution version changes icon" >}} | Solution version changes | Indicates that a [solution module](https://docs.mendix.com/refguide/configure-add-on-and-solution-modules/) used in the app was updated. |

Hover over this column in Studio Pro to get a textual summary of the changes.

### 2.3 Author{#author}

The person who committed the change.

### 2.4 Date{#date}

The date the revision was created, it can have one of the following values:

* **Today** - shown when revision was created today.
* **Yesterday** - shown when revision was created yesterday.
* the date - shown when the revision was created earlier than yesterday.

### 2.5 Time{#time}

The time the revision was created.

### 2.6 Message{#message}

The message saved with the commit. If the message is long, you can read it more easily in the Message tab page, below.

## 3 Details of Revisions

Below the grid are a number of tabs which give further details about the currently-selected revision.

### 3.1 Message

This tab shows the message saved when these changes were committed.

### 3.2 Related Stories

This tab shows a list of stories that are related to the changes.

### 3.3 Changes in Model

This tab shows a list of documents that were changed in the selected revision. From here you can jump to the currently selected changed document by clicking **Go to**, assuming the document still exists in the current version.

The **Mendix version** that was used to commit the revision to the model is also shown. 

### 3.4 Changes on Disk

This tab shows a list of the files that were changed on disk. You can see whether files were added, deleted or modified.

## 4 Read More

* [Version Control](/refguide/version-control/)
* [Stories Pane](/refguide/stories-pane/)
