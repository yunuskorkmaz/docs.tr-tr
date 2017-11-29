---
title: "Nasıl yapılır: ToolStripMenuItems Kopyalama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77f48d7af76cc65092e9045ab76654c96a1a7c02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="f2848-102">Nasıl yapılır: ToolStripMenuItems Kopyalama</span><span class="sxs-lookup"><span data-stu-id="f2848-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="f2848-103">Tasarım zamanında, tüm üst düzey menüleri ve bunların alt öğeleri farklı bir konuma üzerinde kopyalayabilirsiniz <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="f2848-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="f2848-104">Ayrıca, tek tek menü öğeleri üst düzey menüleri arasında kopyalama veya menü öğeleri menü içinde konumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="f2848-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="f2848-105">Bir üst düzey menü ve onun alt öğelerini başka bir üst düzey konumuna kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="f2848-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="f2848-106">Kopyalayın ve CTRL + C tuşlarına basın veya menüyü sağ tıklatın ve seçin istediğiniz menü sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="f2848-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f2848-107">Hedeflenen yeni konumu sonra en üst düzey menü sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce üst düzey menü öğesini sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="f2848-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="f2848-108">Kopyaladığınız menüsü seçili en üst düzey menü önce eklenir.</span><span class="sxs-lookup"><span data-stu-id="f2848-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="f2848-109">Bir üst düzey menü ve onun alt öğelerini açılan konumuna kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="f2848-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="f2848-110">Taşıma ve CTRL + C tuşlarına basın veya menüyü sağ tıklatın ve seçmek için istediğiniz menüyü sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="f2848-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f2848-111">Hedef en üst düzey menüde hedeflenen yeni konumu alt öğenin sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select alt öğeye sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="f2848-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="f2848-112">Kopyaladığınız menü önce seçilen alt öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="f2848-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="f2848-113">Alt menü öğesi için başka bir menüyü kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="f2848-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="f2848-114">Kopyalayın ve CTRL + C tuşlarına basın veya alt menü öğesini sağ tıklatın ve seçin istediğiniz alt öğenin sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="f2848-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="f2848-115">Kesme alt öğeyi içerecek menü sol tıklayın.</span><span class="sxs-lookup"><span data-stu-id="f2848-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="f2848-116">Hedeflenen yeni konumu önce alt öğenin sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce alt öğeye sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="f2848-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="f2848-117">Kopyaladığınız alt öğe, önce seçilen alt öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="f2848-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2848-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f2848-118">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="f2848-119">MenuStrip denetimine genel bakış</span><span class="sxs-lookup"><span data-stu-id="f2848-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
