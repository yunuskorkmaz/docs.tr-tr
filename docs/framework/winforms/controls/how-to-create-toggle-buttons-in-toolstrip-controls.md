---
title: 'Nasıl yapılır: ToolStrip Denetimlerinde İki Durumlu Düğmeler Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toggle buttons [Windows Forms], creating
- examples [Windows Forms], toolbars
- ToolStrip control [Windows Forms], creating toggle buttons
ms.assetid: d9c197df-4c65-43f2-beee-b68b52b2befc
ms.openlocfilehash: 6a003b91cd4db5db2790a20db97dbaa4d8925e96
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972360"
---
# <a name="how-to-create-toggle-buttons-in-toolstrip-controls"></a><span data-ttu-id="e45f3-102">Nasıl yapılır: ToolStrip Denetimlerinde İki Durumlu Düğmeler Oluşturma</span><span class="sxs-lookup"><span data-stu-id="e45f3-102">How to: Create Toggle Buttons in ToolStrip Controls</span></span>

<span data-ttu-id="e45f3-103">Bir Kullanıcı iki durumlu düğmeye tıkladığında, basık görünür ve Kullanıcı düğmeye tekrar tıklaana kadar basık görünümü korur.</span><span class="sxs-lookup"><span data-stu-id="e45f3-103">When a user clicks a toggle button, it appears sunken and retains the sunken appearance until the user clicks the button again.</span></span>

## <a name="to-create-a-toggling-toolstripbutton"></a><span data-ttu-id="e45f3-104">Geçiş bir ToolStripButton oluşturmak için</span><span class="sxs-lookup"><span data-stu-id="e45f3-104">To create a toggling ToolStripButton</span></span>

- <span data-ttu-id="e45f3-105">Aşağıdaki kod örneği gibi bir kod kullanın.</span><span class="sxs-lookup"><span data-stu-id="e45f3-105">Use code such as the following code example.</span></span> <span data-ttu-id="e45f3-106">Bu <xref:System.Windows.Forms.ToolStrip> kod, formunuzun bir denetim içerdiğini ve <xref:System.Windows.Forms.ToolStrip.Items%2A> koleksiyonunun bir <xref:System.Windows.Forms.ToolStripButton> aranan `toolStripButton1`içerdiğini varsayar.</span><span class="sxs-lookup"><span data-stu-id="e45f3-106">This code assumes that your form contains a <xref:System.Windows.Forms.ToolStrip> control, and that its <xref:System.Windows.Forms.ToolStrip.Items%2A> collection contains a <xref:System.Windows.Forms.ToolStripButton> called `toolStripButton1`.</span></span> <span data-ttu-id="e45f3-107">Ayrıca, adlı `toolStripButton1_CheckedChanged`bir olay işleyicisine sahip olduğunuzu varsaymaktadır.</span><span class="sxs-lookup"><span data-stu-id="e45f3-107">It also assumes that you have an event handler called `toolStripButton1_CheckedChanged`.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="e45f3-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e45f3-108">See also</span></span>

- <xref:System.Windows.Forms.ToolStripButton>
- [<span data-ttu-id="e45f3-109">ToolStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="e45f3-109">ToolStrip Control Overview</span></span>](toolstrip-control-overview-windows-forms.md)
