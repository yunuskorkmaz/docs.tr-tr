---
title: "Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bfc1cb718b3738ac93b284b0b438b08d1e721349
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-move-toolstripmenuitems"></a><span data-ttu-id="3c3a0-102">Nasıl yapılır: ToolStripMenuItems Öğelerini Taşıma</span><span class="sxs-lookup"><span data-stu-id="3c3a0-102">How to: Move ToolStripMenuItems</span></span>
<span data-ttu-id="3c3a0-103">Tasarım zamanında tüm üst düzey menü ve bunların menü öğeleri farklı bir konuma taşıyabilir <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-103">At design time, you can move entire top-level menus and their menu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="3c3a0-104">Ayrıca, tek tek menü öğeleri üst düzey menüler arasında Taşı veya menü öğeleri menü içinde konumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-104">You can also move individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c3a0-105">Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza ve ürün sürümüne bağlı olarak Yardım menüsünde açıklanana göre farklılık gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3c3a0-106">Ayarlarınızı değiştirmek için tercih **içeri ve dışarı aktarma ayarları** üzerinde **Araçları** menüsü.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3c3a0-107">Daha fazla bilgi için bkz: [Visual Studio'da geliştirme ayarlarını özelleştirme](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="3c3a0-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-another-top-level-location"></a><span data-ttu-id="3c3a0-108">Bir üst düzey menü ve menü öğelerinden en üst düzey başka bir konuma taşımak için</span><span class="sxs-lookup"><span data-stu-id="3c3a0-108">To move a top-level menu and its menu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="3c3a0-109">Tıklayın ve taşımak istediğiniz menüsünde sol fare düğmesini basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-109">Click and hold down the left mouse button on the menu that you want to move.</span></span>  
  
2.  <span data-ttu-id="3c3a0-110">Hedeflenen yeni konumu önce en üst düzey menü ekleme noktasını sürükleyin ve sol fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-110">Drag the insertion point to the top-level menu that is before the intended new location and release the left mouse button.</span></span>  
  
     <span data-ttu-id="3c3a0-111">Seçili menü ekleme noktasını sağa taşır.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-111">The selected menu moves to the right of the insertion point.</span></span>  
  
### <a name="to-move-a-top-level-menu-and-its-menu-items-to-a-drop-down-location"></a><span data-ttu-id="3c3a0-112">En üst düzey menü ve menü öğelerinin açılan bir konuma taşımak için</span><span class="sxs-lookup"><span data-stu-id="3c3a0-112">To move a top-level menu and its menu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="3c3a0-113">Taşıma ve CTRL + X tuşlarına basın veya menüyü sağ tıklatın ve seçmek için istediğiniz menüyü sol **Kes** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-113">Left-click the menu that you want to move and press CTRL+X, or right-click the menu and select **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="3c3a0-114">Hedef en üst düzey menüde menü öğesi hedeflenen yeni konumu üstünde sol CTRL + V tuşuna basın veya hedeflenen yeni konumu yukarıda menü öğesini sağ tıklatın ve seçin **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-114">In the destination top-level menu, left-click the menu item above the intended new location and press CTRL+V, or right-click the menu item above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="3c3a0-115">Kesme menü sonra seçili menü öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-115">The menu that you cut is inserted after the selected menu item.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-items-collection-editor"></a><span data-ttu-id="3c3a0-116">Menü öğesinin öğeleri koleksiyonu Düzenleyicisi'ni kullanarak bir menü içinde taşımak için</span><span class="sxs-lookup"><span data-stu-id="3c3a0-116">To move a menu item within a menu using the Items Collection Editor</span></span>  
  
1.  <span data-ttu-id="3c3a0-117">Taşımak istediğiniz menü öğesini içeren menüyü sağ tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-117">Right-click the menu that contains the menu item you want to move.</span></span>  
  
2.  <span data-ttu-id="3c3a0-118">Kısayol menüsünden **Düzenle DropDownItems**.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-118">From the shortcut menu, choose **Edit DropDownItems**.</span></span>  
  
3.  <span data-ttu-id="3c3a0-119">İçinde **öğeleri koleksiyonu Düzenleyicisi**, taşımak istediğiniz menü öğesini tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-119">In the **Items Collection Editor**, left-click the menu item you want to move.</span></span>  
  
4.  <span data-ttu-id="3c3a0-120">Menü öğesini menü içinde taşımak için yukarı ve aşağı ok tuşları'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-120">Click the UP and DOWN ARROW keys to move the menu item within the menu.</span></span>  
  
5.  <span data-ttu-id="3c3a0-121">**Tamam**'ı tıklatın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-121">Click **OK**.</span></span>  
  
### <a name="to-move-a-menu-item-within-a-menu-using-the-keyboard"></a><span data-ttu-id="3c3a0-122">Menü öğesi için klavyeyi kullanma menü içinde taşımak için</span><span class="sxs-lookup"><span data-stu-id="3c3a0-122">To move a menu item within a menu using the keyboard</span></span>  
  
1.  <span data-ttu-id="3c3a0-123">ALT tuşunu basılı yeniden açın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-123">Press and hold down the ALT key.</span></span>  
  
2.  <span data-ttu-id="3c3a0-124">' A tıklayın ve taşımak istediğiniz menü öğesini sol fare düğmesini basılı tutun.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-124">Click and hold the left mouse button on the menu item that you want to move.</span></span>  
  
3.  <span data-ttu-id="3c3a0-125">Menü öğesinin yeni bir konuma sürükleyin ve sol fare düğmesini bırakın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-125">Drag the menu item to the new location and release the left mouse button.</span></span>  
  
### <a name="to-move-a-menu-item-to-another-menu"></a><span data-ttu-id="3c3a0-126">Menü öğesi için başka bir menüyü taşımak için</span><span class="sxs-lookup"><span data-stu-id="3c3a0-126">To move a menu item to another menu</span></span>  
  
1.  <span data-ttu-id="3c3a0-127">Taşıma ve CTRL + X tuşlarına basın veya menü öğesini sağ tıklatın ve seçin istediğiniz menü öğesi sol **Kes** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-127">Left-click the menu item that you want to move and press CTRL+X, or right-click the menu item and choose **Cut** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="3c3a0-128">Kesme menü öğesi içerecek menü sol tıklayın.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-128">Left-click the menu that will contain the menu item that you cut.</span></span>  
  
3.  <span data-ttu-id="3c3a0-129">Önce hedeflenen yeni konumu menü öğesini tıklatın ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce menü öğesini sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-129">Left-click the menu item that is before the intended new location and press CTRL+V, or right-click the menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="3c3a0-130">Kesme menü öğesi seçili menü öğesi sonra eklenir.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-130">The menu item that you cut is inserted after the selected menu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c3a0-131">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3c3a0-131">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="3c3a0-132">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="3c3a0-132">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
