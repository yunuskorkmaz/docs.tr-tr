---
title: 'Nasıl yapılır: ToolStripMenuItems Kopyalama'
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: 238516f18037a75b1d254d95086e22a970fadf09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530487"
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="eeceb-102">Nasıl yapılır: ToolStripMenuItems Kopyalama</span><span class="sxs-lookup"><span data-stu-id="eeceb-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="eeceb-103">Tasarım zamanında, tüm üst düzey menüleri ve bunların alt öğeleri farklı bir konuma üzerinde kopyalayabilirsiniz <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="eeceb-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="eeceb-104">Ayrıca, tek tek menü öğeleri üst düzey menüleri arasında kopyalama veya menü öğeleri menü içinde konumunu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="eeceb-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="eeceb-105">Bir üst düzey menü ve onun alt öğelerini başka bir üst düzey konumuna kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="eeceb-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="eeceb-106">Kopyalayın ve CTRL + C tuşlarına basın veya menüyü sağ tıklatın ve seçin istediğiniz menü sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="eeceb-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="eeceb-107">Hedeflenen yeni konumu sonra en üst düzey menü sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce üst düzey menü öğesini sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="eeceb-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="eeceb-108">Kopyaladığınız menüsü seçili en üst düzey menü önce eklenir.</span><span class="sxs-lookup"><span data-stu-id="eeceb-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="eeceb-109">Bir üst düzey menü ve onun alt öğelerini açılan konumuna kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="eeceb-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="eeceb-110">Taşıma ve CTRL + C tuşlarına basın veya menüyü sağ tıklatın ve seçmek için istediğiniz menüyü sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="eeceb-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="eeceb-111">Hedef en üst düzey menüde hedeflenen yeni konumu alt öğenin sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select alt öğeye sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="eeceb-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="eeceb-112">Kopyaladığınız menü önce seçilen alt öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="eeceb-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="eeceb-113">Alt menü öğesi için başka bir menüyü kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="eeceb-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="eeceb-114">Kopyalayın ve CTRL + C tuşlarına basın veya alt menü öğesini sağ tıklatın ve seçin istediğiniz alt öğenin sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="eeceb-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="eeceb-115">Kesme alt öğeyi içerecek menü sol tıklayın.</span><span class="sxs-lookup"><span data-stu-id="eeceb-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="eeceb-116">Hedeflenen yeni konumu önce alt öğenin sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce alt öğeye sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="eeceb-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="eeceb-117">Kopyaladığınız alt öğe, önce seçilen alt öğesi eklenir.</span><span class="sxs-lookup"><span data-stu-id="eeceb-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeceb-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eeceb-118">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [<span data-ttu-id="eeceb-119">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="eeceb-119">MenuStrip Control Overview</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
