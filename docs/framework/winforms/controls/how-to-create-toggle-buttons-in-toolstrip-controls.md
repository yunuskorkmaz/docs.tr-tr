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
ms.openlocfilehash: a059726ea410e88121a0b755295c3c492c11962a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705525"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="a1aee-102">Nasıl yapılır: ToolStrip denetimlerinde iki durumlu düğmeler oluşturma</span><span class="sxs-lookup"><span data-stu-id="a1aee-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>
<span data-ttu-id="a1aee-103">Bir kullanıcı bir iki durumlu düğmeyi tıkladığında basık görünür ve kullanıcı yeniden düğmesine tıklayana kadar basık görünümü korur.</span><span class="sxs-lookup"><span data-stu-id="a1aee-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>  
  
### <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="a1aee-104">Toggling ToolStripButton oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="a1aee-104">To create a toggling ToolStripButton</span></span>  
  
-   <span data-ttu-id="a1aee-105">Aşağıdaki kod örneği gibi bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="a1aee-105">Use code such as the following code example.</span></span> <span data-ttu-id="a1aee-106">Bu kod, formunuzu içerdiğini varsaymaktadır bir <xref:System.Windows.Forms.ToolStrip> denetimi ve kendi <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonu içeren bir <xref:System.Windows.Forms.ToolStripButton> adlı `toolStripButton1`.</span><span class="sxs-lookup"><span data-stu-id="a1aee-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="a1aee-107">Ayrıca, adlı bir olay işleyicisi sahibi olduğunuzu varsayar `toolStripButton1_CheckedChanged`.</span><span class="sxs-lookup"><span data-stu-id="a1aee-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a1aee-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1aee-108">See also</span></span>
- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="a1aee-109">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a1aee-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
