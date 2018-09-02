---
title: 'Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma'
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], moving
- menus [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], dragging and dropping
- menu items [Windows Forms], moving
- menu items [Windows Forms], cutting and pasting
- menu items [Windows Forms], dragging and dropping
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], cutting and pasting
ms.assetid: cab9e03e-4edd-4c25-b3e3-bd1edc602bd9
ms.openlocfilehash: 69ef2bbaa05155532887897a0aef79a778594169
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384906"
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="441d2-102">Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma</span><span class="sxs-lookup"><span data-stu-id="441d2-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="441d2-103">Tasarım zamanında, tüm üst düzey menüler ve menü öğeleri, farklı bir konuma taşıyabilirsiniz <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="441d2-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="441d2-104">Ayrıca, tek tek menü öğeleri üst düzey menüler arasında Taşı veya menü öğeleri içindeki konumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="441d2-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="441d2-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="441d2-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="441d2-106">Ayarlarınızı değiştirmek için seçin **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="441d2-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="441d2-107">Daha fazla bilgi için [Visual Studio IDE'yi kişiselleştirme](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="441d2-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="441d2-108">Üst düzey menü ve menü öğelerinden, üst düzey başka bir konuma taşımak için</span><span class="sxs-lookup"><span data-stu-id="441d2-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="441d2-109">' A tıklayın ve taşımak istediğiniz menüsünde sol fare düğmesini basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="441d2-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="441d2-110">Ekleme noktasını amaçlanan yeni konum önce üst düzey menü sürükleyin ve sol fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="441d2-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="441d2-111">Seçili menü ekleme noktasını sağa taşır.</span><span class="sxs-lookup"><span data-stu-id="441d2-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="441d2-112">Üst düzey menü ve menü öğelerinden bir açılan konuma taşımak için</span><span class="sxs-lookup"><span data-stu-id="441d2-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="441d2-113">Taşıma ve CTRL + X tuşlarına basın veya menü sağ tıklayıp istediğiniz menü sol **Kes** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="441d2-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="441d2-114">Hedef üst düzey menüsündeki menü öğesi üzerinde istenen yeni konumu sol ve CTRL + V tuşlarına basın veya menü öğesi üzerinde istenen konuma sağ tıklayıp **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="441d2-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="441d2-115">Kesme menü, seçili menü öğesini sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="441d2-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="441d2-116">Bir menü öğesi içinde öğeler Koleksiyonu Düzenleyicisi'ni kullanarak bir menüyü taşımak için</span><span class="sxs-lookup"><span data-stu-id="441d2-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="441d2-117">Taşımak istediğiniz menü öğesini içeren menü sağ tıklayın.</span><span class="sxs-lookup"><span data-stu-id="441d2-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="441d2-118">Kısayol menüsünden **Düzenle DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="441d2-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="441d2-119">İçinde **öğeler Koleksiyonu Düzenleyicisi**, taşımak istediğiniz menü öğesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="441d2-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="441d2-120">Menü öğesinin menü içinde taşımak için yukarı ve aşağı ok tuşlarını tıklayın.</span><span class="sxs-lookup"><span data-stu-id="441d2-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="441d2-121">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="441d2-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="441d2-122">Bir menü öğesi içindeki klavyeyi kullanarak taşımak için</span><span class="sxs-lookup"><span data-stu-id="441d2-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="441d2-123">ALT tuşunu basılı yeniden açın.</span><span class="sxs-lookup"><span data-stu-id="441d2-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="441d2-124">Tıklayın ve taşımak istediğiniz menü öğesini sol fare düğmesini basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="441d2-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="441d2-125">Menü öğesi yeni konuma sürükleyin ve sol fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="441d2-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="441d2-126">Bir menü öğesi için başka bir menüyü taşımak için</span><span class="sxs-lookup"><span data-stu-id="441d2-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="441d2-127">Taşıma ve CTRL + X tuşlarına basın veya menü öğesini sağ tıklatın ve seçin için istediğiniz menü öğesini sol **Kes** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="441d2-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="441d2-128">Kesme menü öğesini içeren menüsünü tıklatın.</span><span class="sxs-lookup"><span data-stu-id="441d2-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="441d2-129">Önce hedeflenen yeni konum menü öğesini tıklatın ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce bir menü öğesini sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="441d2-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="441d2-130">Kesme menü öğesi, seçili bir menü öğesi sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="441d2-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="441d2-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="441d2-131">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="441d2-132">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="441d2-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
