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
ms.openlocfilehash: f86a2934e799e4604693491dacbecc517d44d810
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046220"
---
# <a name="how-to-disable-toolstripmenuitems"></a><span data-ttu-id="c39df-102">Nasıl yapılır: ToolStripMenuItems'ı Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="c39df-102">How to: Disable ToolStripMenuItems</span></span>
<span data-ttu-id="c39df-103">Kullanıcı etkinliklerine yanıt olarak menü öğelerini etkinleştirip devre dışı bırakarak bir kullanıcının yapabiliriz olan komutları sınırlayabilirsiniz veya genişletebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c39df-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="c39df-104">Menü öğeleri oluşturulduklarında varsayılan olarak etkindir, ancak bu <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özellik aracılığıyla ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="c39df-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="c39df-105">Bu özelliği tasarım zamanında **Özellikler** penceresinde veya program aracılığıyla kod içinde ayarlayarak düzenleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c39df-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span>  
  
### <a name="to-disable-a-menu-item-programmatically"></a><span data-ttu-id="c39df-106">Bir menü öğesini programlı olarak devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="c39df-106">To disable a menu item programmatically</span></span>  
  
- <span data-ttu-id="c39df-107">Menü öğesinin özelliklerini ayarladığınız yöntemi içinde, <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini olarak `false`ayarlamak için kod ekleyin.</span><span class="sxs-lookup"><span data-stu-id="c39df-107">Within the method where you set the properties of the menu item, add code to set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
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
    > <span data-ttu-id="c39df-108">Bir menüdeki ilk veya üst düzey menü öğesini devre dışı bırakmak, menüdeki tüm menü öğelerini gizler, ancak devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c39df-108">Disabling the first or top-level menu item in a menu hides all the menu items contained within the menu, but does not disable them.</span></span> <span data-ttu-id="c39df-109">Benzer şekilde, alt menü öğelerinin bulunduğu bir menü öğesini devre dışı bırakmak alt menü öğelerini gizler, ancak devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="c39df-109">Likewise, disabling a menu item that has submenu items hides the submenu items, but does not disable them.</span></span> <span data-ttu-id="c39df-110">Belirli bir menüdeki tüm komutlar Kullanıcı için kullanılabilir durumda değilse, tüm menüyü gizleme ve devre dışı bırakma, bu da temiz bir kullanıcı arabirimi sunan için iyi bir programlama uygulaması kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="c39df-110">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="c39df-111">Menüyü gizlemeniz ve devre dışı bırakmanız ve menü içindeki her öğe ve alt menü öğesini devre dışı bırakmanız gerekir, çünkü tek tek gizleme, kısayol tuşu aracılığıyla bir menü komutuna erişimi engellemez.</span><span class="sxs-lookup"><span data-stu-id="c39df-111">You should hide and disable the menu, and disable every item and submenu item in the menu, because hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="c39df-112">Tüm menüyü gizlemek için üst düzey menü öğesinin `false` özelliğiniolarakayarlayın.<xref:System.Windows.Forms.ToolStripItem.Visible%2A></span><span class="sxs-lookup"><span data-stu-id="c39df-112">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c39df-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c39df-113">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="c39df-114">Nasıl yapılır: ToolStripMenuItems 'ı gizle</span><span class="sxs-lookup"><span data-stu-id="c39df-114">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="c39df-115">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c39df-115">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
