---
title: 'Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Devre Dışı Bırakma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 9965825458afcd50b29699c3b89ed506078e04d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59338065"
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a><span data-ttu-id="27987-102">Nasıl yapılır: Tasarımcıyı Kullanarak ToolStripMenuItems’ı Devre Dışı Bırakma</span><span class="sxs-lookup"><span data-stu-id="27987-102">How to: Disable ToolStripMenuItems Using the Designer</span></span>
<span data-ttu-id="27987-103">Sınırlamak veya bir kullanıcı, kullanıcı etkinlikleri için yanıt menü öğelerini devre dışı bırakma ve etkinleştirme yapabilir komutları alanlarını genişletmeniz mümkün değildir.</span><span class="sxs-lookup"><span data-stu-id="27987-103">You can limit or broaden the commands a user may make by enabling and disabling menu items in response to user activities.</span></span> <span data-ttu-id="27987-104">Menü öğeleri, varsayılan olarak etkinleştirilir, bunlar oluşturulur, ancak bu aracılığıyla ayarlanabilir <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="27987-104">Menu items are enabled by default when they are created, but this can be adjusted through the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property.</span></span> <span data-ttu-id="27987-105">Bu özellik tasarım zamanında işleyebileceğiniz **özellikleri** penceresi veya program aracılığıyla kod içinde ayarlama.</span><span class="sxs-lookup"><span data-stu-id="27987-105">You can manipulate this property at design time in the **Properties** window or programmatically by setting it in code.</span></span> <span data-ttu-id="27987-106">Daha fazla bilgi için [nasıl yapılır: Toolstripmenuıtems öğelerini devre dışı](how-to-disable-toolstripmenuitems.md).</span><span class="sxs-lookup"><span data-stu-id="27987-106">For more information, see [How to: Disable ToolStripMenuItems](how-to-disable-toolstripmenuitems.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27987-107">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="27987-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="27987-108">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="27987-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="27987-109">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="27987-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-disable-a-menu-item-at-design-time"></a><span data-ttu-id="27987-110">Tasarım zamanında bir menü öğesi devre dışı bırakmak için</span><span class="sxs-lookup"><span data-stu-id="27987-110">To disable a menu item at design time</span></span>  
  
1. <span data-ttu-id="27987-111">Formda Seçili Menü öğesiyle ayarlamak <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> özelliğini `false`.</span><span class="sxs-lookup"><span data-stu-id="27987-111">With the menu item selected on the form, set the <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> property to `false`.</span></span>  
  
    > [!TIP]
    >  <span data-ttu-id="27987-112">Bir menü ilk veya üst düzey menü öğesi devre dışı bırakma içinde menüyü içeren bütün menü öğelerini devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="27987-112">Disabling the first or top-level menu item in a menu disables all the menu items contained within the menu.</span></span> <span data-ttu-id="27987-113">Benzer şekilde, alt öğeleri alt öğeleri içeren bir menü öğesi devre dışı bırakma devre dışı bırakır.</span><span class="sxs-lookup"><span data-stu-id="27987-113">Likewise, disabling a menu item that has submenu items disables the submenu items.</span></span> <span data-ttu-id="27987-114">Kullanıcıya verilen menüsündeki tüm komutları kullanılamıyorsa, bunu bir temiz kullanıcı arabirimi sunar gibi hem gizlemek ve tüm menü devre dışı bırakmak için iyi bir programlama uygulama kabul edilir.</span><span class="sxs-lookup"><span data-stu-id="27987-114">If all the commands on a given menu are unavailable to the user, it is considered good programming practice to both hide and disable the entire menu, as this presents a clean user interface.</span></span> <span data-ttu-id="27987-115">Gizleme hem tek başına bir gizleme için bir menü komutu bir kısayol tuşu aracılığıyla erişimi engellemez menüsü devre dışı bırakın.</span><span class="sxs-lookup"><span data-stu-id="27987-115">You should both hide and disable the menu, as hiding alone does not prevent access to a menu command via a shortcut key.</span></span> <span data-ttu-id="27987-116">Ayarlama <xref:System.Windows.Forms.ToolStripItem.Visible%2A> özelliği için bir üst düzey menü öğesinin `false` tüm menü gizlemek için.</span><span class="sxs-lookup"><span data-stu-id="27987-116">Set the <xref:System.Windows.Forms.ToolStripItem.Visible%2A> property of a top-level menu item to `false` to hide the entire menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27987-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27987-117">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="27987-118">Nasıl yapılır: Toolstripmenuıtems gizleme</span><span class="sxs-lookup"><span data-stu-id="27987-118">How to: Hide ToolStripMenuItems</span></span>](how-to-hide-toolstripmenuitems.md)
- [<span data-ttu-id="27987-119">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="27987-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
