---
title: "Nasıl yapılır: ToolStripMenuItems'ı Devre Dışı Bırakma"
ms.date: 03/30/2017
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
ms.openlocfilehash: a480cd29eef1a79a69f702eed7cd02c28d7ea3de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954238"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="a5b7d-102">Nasıl yapılır: ToolStripMenuItems'ı Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="a5b7d-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="a5b7d-103">Sınırlamak veya bir kullanıcı, kullanıcı etkinlikleri için yanıt menü öğelerini devre dışı bırakma ve etkinleştirme yapabilir komutları alanlarını genişletmeniz mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="a5b7d-104">Menü öğeleri, varsayılan olarak etkinleştirilir, bunlar oluşturulur, ancak bu aracılığıyla ayarlanabilir <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="a5b7d-105">Bu özellik tasarım zamanında işleyebileceğiniz **özellikleri** penceresi veya program aracılığıyla kod içinde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="a5b7d-106">Program aracılığıyla bir menü öğesi devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="a5b7d-106">To disable a menu item programmatically</span></span>  
  
- <span data-ttu-id="a5b7d-107">Menü öğesi özelliklerini ayarladığınız yöntemi içinde ayarlamak üzere kod eklemek <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
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
    >  <span data-ttu-id="a5b7d-108">Bir menü ilk veya üst düzey menü öğesi devre dışı bırakma içinde menüyü içeren bütün menü öğelerini gizler, ancak bunları devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="a5b7d-109">Benzer şekilde, alt öğelerine sahip bir menü öğesi devre dışı bırakma alt öğeleri gizler, ancak bunları devre dışı bırakmaz.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="a5b7d-110">Kullanıcıya verilen menüsündeki tüm komutları kullanılamıyorsa, bunu bir temiz kullanıcı arabirimi sunar gibi hem gizlemek ve tüm menü devre dışı bırakmak için iyi bir programlama uygulama kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="a5b7d-111">Gizleme ve menüsünü devre dışı bırak ve tek başına gizleme erişim için bir kısayol tuşu ile bir menü komutu engellemez çünkü her öğe ve alt öğesi menüsündeki devre dışı bırakmak gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="a5b7d-112">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği için bir üst düzey menü öğesinin `false` tüm menü gizlemek için.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5b7d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5b7d-113">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="a5b7d-114">Nasıl yapılır: Toolstripmenuıtems gizleme</span><span class="sxs-lookup"><span data-stu-id="a5b7d-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="a5b7d-115">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a5b7d-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
