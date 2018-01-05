---
title: "Nasıl yapılır: ToolStrip Denetimlerinde İki Durumlu Düğmeler Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5547b35bda8054b3ca41435e04855408d8a77c8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="811fd-102">Nasıl yapılır: ToolStrip Denetimlerinde İki Durumlu Düğmeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="811fd-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="811fd-103">Bir kullanıcı iki durumlu düğme tıkladığında, basık görünür ve kullanıcı yeniden düğmesine tıklar kadar basık görünümünü korur.</span><span class="sxs-lookup"><span data-stu-id="811fd-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="811fd-104">Toggling ToolStripButton oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="811fd-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="811fd-105">Aşağıdaki kod örneğinde gibi kodunu kullanın.</span><span class="sxs-lookup"><span data-stu-id="811fd-105">Use code such as the following code example.</span></span> <span data-ttu-id="811fd-106">Bu kod, form içerdiğini varsayar bir <xref:System.Windows.Forms.ToolStrip> denetim ve onun <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonu içeren bir <xref:System.Windows.Forms.ToolStripButton> adlı `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="811fd-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="811fd-107">Ayrıca, adlı bir olay işleyicisi sahibi olduğunuzu varsayar `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="811fd-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="811fd-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="811fd-108">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripButton>  
 [<span data-ttu-id="811fd-109">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="811fd-109">ToolStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
