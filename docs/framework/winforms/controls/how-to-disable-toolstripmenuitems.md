---
title: "Nasıl yapılır: ToolStripMenuItems'ni Devre Dışı Bırakma"
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
- cpp
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], enabling
- ToolStripMenuItems [Windows Forms], disabling
- menu items [Windows Forms], disabling
- disabling menu items
- menu items [Windows Forms], enabling
- menus [Windows Forms], disabling menu items
ms.assetid: bcc1da84-50fd-41d2-8475-103b581d5654
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0432c59979f8f595b481154f5b339e448ee66b06
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="77ab8-102">Nasıl yapılır: ToolStripMenuItems'ni Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="77ab8-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="77ab8-103">Sınırlandırmak veya bir kullanıcı tarafından etkinleştirme ve kullanıcı etkinlikleri yanıtta menü öğelerini devre dışı bırakma hale getirebilir komutları genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="77ab8-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="77ab8-104">Menü öğeleri, varsayılan olarak etkinleştirilir, oluşturuldukları, ancak bu aracılığıyla ayarlanabilir <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="77ab8-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="77ab8-105">Tasarım zamanında bu özellik işleyebilir **özellikleri** penceresi veya programlı olarak ayarlayarak bu kodu.</span><span class="sxs-lookup"><span data-stu-id="77ab8-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="77ab8-106">Menü öğesi program aracılığıyla devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="77ab8-106">To disable a menu item programmatically</span></span>  
  
-   <span data-ttu-id="77ab8-107">Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak için kod ekleme <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="77ab8-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    ```vb  
    MenuItem1.Enabled = False  
    ```  
  
    ```csharp  
    menuItem1.Enabled = false;  
    ```  
  
    ```cpp  
    menuItem1->Enabled = false;  
    ```  
  
    > [!TIP]
    >  <span data-ttu-id="77ab8-108">Bir menüdeki ilk ya da üst düzey menü öğesini devre dışı bırakma menüsünün içinde yer alan tüm menü öğelerini gizler, ancak bunları devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="77ab8-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="77ab8-109">Benzer şekilde, alt öğelerine sahip bir menü öğesini devre dışı bırakma alt öğeleri gizler, ancak bunları devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="77ab8-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="77ab8-110">Verilen menüsünde tüm komutlar kullanıcıya kullanılabilir durumda değilse, bu bir temiz kullanıcı arabirimi sunar gibi Gizle hem tüm menü devre dışı bırakmak için iyi bir programlama uygulama kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="77ab8-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="77ab8-111">Gizleme ve menüsünü devre dışı bırak ve tek başına gizleme erişimi için bir kısayol tuşu aracılığıyla menü komutu engellemez çünkü her öğeyi ve alt öğesi menüde devre dışı bırakmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="77ab8-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="77ab8-112">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> bir üst düzey menü öğesine özelliğinin `false` tüm menü gizlemek için.</span><span class="sxs-lookup"><span data-stu-id="77ab8-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77ab8-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="77ab8-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="77ab8-114">Nasıl yapılır: ToolStripMenuItems Gizleme</span><span class="sxs-lookup"><span data-stu-id="77ab8-114">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="77ab8-115">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="77ab8-115">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
