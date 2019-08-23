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
ms.openlocfilehash: 7ef3fe1210ae42c52a4fd7f23633d6566bc102a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956056"
---
# <a name="how-to-split-a-window-horizontally"></a>Nasıl yapılır: Pencereyi Yatay Bölme
Aşağıdaki kod örneği, <xref:System.Windows.Forms.SplitContainer> denetimi yatay olarak bölen ayırıcıyı yapar.  
  
> [!NOTE]
> <xref:System.Windows.Forms.SplitContainer> Denetimin özelliği, denetimin kendisinin değil, ayırıcının yönünü belirler. <xref:System.Windows.Forms.SplitContainer.Orientation%2A>  
  
### <a name="to-split-a-window-horizontally"></a>Pencereyi yatay olarak bölme  
  
1. Bir yordam içinde, <xref:System.Windows.Forms.SplitContainer.Orientation%2A> <xref:System.Windows.Forms.SplitContainer> denetimin özelliğini olarak <xref:System.Windows.Forms.Orientation.Horizontal>ayarlayın.  
  
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
