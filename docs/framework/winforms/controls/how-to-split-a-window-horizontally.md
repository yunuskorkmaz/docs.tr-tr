---
title: 'Nasıl yapılır: Pencereyi yatay bölme'
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
ms.openlocfilehash: 651e265b337b106779aeefdfa49decd3725f1a53
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701462"
---
# <a name="how-to-split-a-window-horizontally"></a><span data-ttu-id="900e5-102">Nasıl yapılır: Pencereyi yatay bölme</span><span class="sxs-lookup"><span data-stu-id="900e5-102">How to: Split a Window Horizontally</span></span>
<span data-ttu-id="900e5-103">Aşağıdaki kod örneği böler Bölümlendirici yapar <xref:System.Windows.Forms.SplitContainer> denetimi yatay.</span><span class="sxs-lookup"><span data-stu-id="900e5-103">The following code example makes the splitter that divides the <xref:System.Windows.Forms.SplitContainer> control horizontal.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="900e5-104"><xref:System.Windows.Forms.SplitContainer.Orientation%2A> Özelliği <xref:System.Windows.Forms.SplitContainer> denetimi Bölümlendiricinin, Denetim'ın yönü belirler.</span><span class="sxs-lookup"><span data-stu-id="900e5-104">The <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control determines the direction of the splitter, not of the control itself.</span></span>  
  
### <a name="to-split-a-window-horizontally"></a><span data-ttu-id="900e5-105">Pencereyi yatay bölme için</span><span class="sxs-lookup"><span data-stu-id="900e5-105">To split a window horizontally</span></span>  
  
1.  <span data-ttu-id="900e5-106">Bir yordam içinde ayarlamak <xref:System.Windows.Forms.SplitContainer.Orientation%2A> özelliği <xref:System.Windows.Forms.SplitContainer> denetimini <xref:System.Windows.Forms.Orientation.Horizontal>.</span><span class="sxs-lookup"><span data-stu-id="900e5-106">Within a procedure, set the <xref:System.Windows.Forms.SplitContainer.Orientation%2A> property of the <xref:System.Windows.Forms.SplitContainer> control to <xref:System.Windows.Forms.Orientation.Horizontal>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="900e5-107">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="900e5-107">See also</span></span>
- <xref:System.Windows.Forms.SplitContainer>
- [<span data-ttu-id="900e5-108">SplitContainer Denetimi</span><span class="sxs-lookup"><span data-stu-id="900e5-108">SplitContainer Control</span></span>](../../../../docs/framework/winforms/controls/splitcontainer-control-windows-forms.md)
