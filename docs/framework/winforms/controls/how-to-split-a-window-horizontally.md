---
title: 'Nasıl yapılır: Pencereyi Yatay Bölme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SplitContainer control [Windows Forms], horizontal splitter
- splitter windows [Windows Forms], changing splitter orientation
- splitter windows [Windows Forms], horizontal
- windows [Windows Forms], splitting horizontally
ms.assetid: a1f74f29-048c-4723-85fa-b9d375ab8f4b
ms.openlocfilehash: d10616e2f09eabec1209a26aabe501ea0af903cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189661"
---
# <a name="how-to-split-a-window-horizontally"></a>Nasıl yapılır: Pencereyi Yatay Bölme
Aşağıdaki kod örneği böler Bölümlendirici yapar <xref:System.Windows.Forms.SplitContainer> denetimi yatay.  
  
> [!NOTE]
>  <xref:System.Windows.Forms.SplitContainer.Orientation%2A> Özelliği <xref:System.Windows.Forms.SplitContainer> denetimi Bölümlendiricinin, Denetim'ın yönü belirler.  
  
### <a name="to-split-a-window-horizontally"></a>Pencereyi yatay bölme için  
  
1.  Bir yordam içinde ayarlamak <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliği <xref:System.Windows.Forms.SplitContainer> denetimini <xref:System.Windows.Forms.Orientation.Horizontal>.  
  
    ```vb  
    Sub ShowSplitContainer()  
        Dim splitContainer1 as new SplitContainer()  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D  
        splitContainer1.Location = New System.Drawing.Point(74, 20)  
        splitContainer1.Name = "DemoSplitContainer"  
        splitContainer1.Size = New System.Drawing.Size(212, 435)  
        splitContainer1.TabIndex = 0  
        splitContainer1.Orientation = Orientation.Horizontal  
        Controls.Add(splitContainer1)  
    End Sub  
    ```  
  
    ```csharp  
    public void showSplitContainer()  
    {  
        SplitContainer splitContainer1 = new SplitContainer ();  
        splitContainer1.BorderStyle = BorderStyle.Fixed3D;  
        splitContainer1.Location = new System.Drawing.Point (74, 20);  
        splitContainer1.Name = "DemoSplitContainer";  
        splitContainer1.Size = new System.Drawing.Size (212, 435);  
        splitContainer1.TabIndex = 0;  
        splitContainer1.Orientation = Orientation.Horizontal;  
        this.Controls.Add (splitContainer1);  
  
    }  
    ```  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.SplitContainer>
- [SplitContainer Denetimi](splitcontainer-control-windows-forms.md)
