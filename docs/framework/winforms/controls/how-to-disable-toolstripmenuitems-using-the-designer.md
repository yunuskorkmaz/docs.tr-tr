---
title: "Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems Öğelerini Devre Dışı Bırakma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4958f315ff0415c3964d22dffff2553c0901eb91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="5eab0-102">Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems Öğelerini Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="5eab0-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="5eab0-103">Sınırlandırmak veya bir kullanıcı tarafından etkinleştirme ve kullanıcı etkinlikleri yanıtta menü öğelerini devre dışı bırakma hale getirebilir komutları genişletebilir.</span><span class="sxs-lookup"><span data-stu-id="5eab0-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="5eab0-104">Menü öğeleri, varsayılan olarak etkinleştirilir, oluşturuldukları, ancak bu aracılığıyla ayarlanabilir <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5eab0-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="5eab0-105">Tasarım zamanında bu özellik işleyebilir **özellikleri** penceresi veya programlı olarak ayarlayarak bu kodu.</span><span class="sxs-lookup"><span data-stu-id="5eab0-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="5eab0-106">Daha fazla bilgi için bkz: [nasıl yapılır: Toolstripmenuıtems devre dışı](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="5eab0-106">For more information, see [How to: Disable ToolStripMenuItems](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5eab0-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="5eab0-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="5eab0-108">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="5eab0-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="5eab0-109">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="5eab0-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="5eab0-110">Tasarım zamanında bir menü öğesini devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="5eab0-110">To disable a menu item at design time</span></span>  
  
1.  <span data-ttu-id="5eab0-111">Menü öğesi formunda seçili ayarlamak <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğine `false`.</span><span class="sxs-lookup"><span data-stu-id="5eab0-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="5eab0-112">Bir menüdeki ilk ya da üst düzey menü öğesini devre dışı bırakma menüsünün içinde yer alan tüm menü öğelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5eab0-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="5eab0-113">Benzer şekilde, alt öğeleri alt öğelerine sahip bir menü öğesini devre dışı bırakma devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="5eab0-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="5eab0-114">Verilen menüsünde tüm komutlar kullanıcıya kullanılabilir durumda değilse, bu bir temiz kullanıcı arabirimi sunar gibi Gizle hem tüm menü devre dışı bırakmak için iyi bir programlama uygulama kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="5eab0-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="5eab0-115">Gizleme hem tek başına bir gizleme erişimi bir kısayol tuşu aracılığıyla menü komutu engellemez menüsünde devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="5eab0-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="5eab0-116">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> bir üst düzey menü öğesine özelliğinin `false` tüm menü gizlemek için.</span><span class="sxs-lookup"><span data-stu-id="5eab0-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5eab0-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5eab0-117">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="5eab0-118">Nasıl yapılır: Toolstripmenuıtems</span><span class="sxs-lookup"><span data-stu-id="5eab0-118">How to: Hide ToolStripMenuItems</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [<span data-ttu-id="5eab0-119">MenuStrip denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="5eab0-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
