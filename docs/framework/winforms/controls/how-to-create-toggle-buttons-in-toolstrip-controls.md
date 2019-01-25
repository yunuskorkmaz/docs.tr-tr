---
title: 'Nasıl yapılır: ToolStrip denetimlerinde iki durumlu düğmeler oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 723916eb0c1e242df301c49bf0716e0262a3ba42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54614984"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="fadfa-102">Nasıl yapılır: ToolStrip denetimlerinde iki durumlu düğmeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="fadfa-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="fadfa-103">Bir kullanıcı bir iki durumlu düğmeyi tıkladığında basık görünür ve kullanıcı yeniden düğmesine tıklayana kadar basık görünümü korur.</span><span class="sxs-lookup"><span data-stu-id="fadfa-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="fadfa-104">Toggling ToolStripButton oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="fadfa-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="fadfa-105">Aşağıdaki kod örneği gibi bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="fadfa-105">Use code such as the following code example.</span></span> <span data-ttu-id="fadfa-106">Bu kod, formunuzu içerdiğini varsaymaktadır bir <xref:System.Windows.Forms.ToolStrip> denetimi ve kendi <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonu içeren bir <xref:System.Windows.Forms.ToolStripButton> adlı `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="fadfa-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="fadfa-107">Ayrıca, adlı bir olay işleyicisi sahibi olduğunuzu varsayar `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="fadfa-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
    ```vb  
    toolStripButton1.CheckOnClick = True  
    toolStripButton1.CheckedChanged AddressOf _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
    ```csharp  
    toolStripButton1.CheckOnClick = true;  
    toolStripButton1.CheckedChanged += new _  
    EventHandler(toolStripButton1_CheckedChanged);  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="fadfa-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fadfa-108">See also</span></span>
- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="fadfa-109">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fadfa-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
