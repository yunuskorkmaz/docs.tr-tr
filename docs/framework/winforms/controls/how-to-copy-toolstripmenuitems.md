---
title: 'Nasıl yapılır: Toolstripmenuıtems kopyalama'
ms.date: 03/30/2017
helpviewer_keywords:
- menu items [Windows Forms], copying and pasting
- MenuStrip control [Windows Forms], arranging items
- ToolStripMenuItems [Windows Forms], copying and pasting
ms.assetid: 17ef4207-e92e-4db2-b648-27246e6517ad
ms.openlocfilehash: 18077f542b1b49f8e81e68fc1e7a5d3e1e417a21
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713884"
---
# <a name="how-to-copy-toolstripmenuitems"></a><span data-ttu-id="4d672-102">Nasıl yapılır: Toolstripmenuıtems kopyalama</span><span class="sxs-lookup"><span data-stu-id="4d672-102">How to: Copy ToolStripMenuItems</span></span>
<span data-ttu-id="4d672-103">Tasarım zamanında, tüm üst düzey menüler ve bunların alt öğeleri farklı bir konuma üzerinde kopyalayabilirsiniz <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="4d672-103">At design time, you can copy entire top-level menus and their submenu items to a different place on the <xref:System.Windows.Forms.MenuStrip>.</span></span> <span data-ttu-id="4d672-104">Ayrıca, tek tek menü öğeleri üst düzey menüler arasında kopyalama veya içindeki menü öğelerinin konumu değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="4d672-104">You can also copy individual menu items between top-level menus or change the position of menu items within a menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-another-top-level-location"></a><span data-ttu-id="4d672-105">Üst düzey menü ve onun alt öğelerini başka bir üst düzey konumuna kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="4d672-105">To copy a top-level menu and its submenu items to another top-level location</span></span>  
  
1.  <span data-ttu-id="4d672-106">Kopyala ve CTRL + C tuşlarına basın veya menü sağ tıklayıp istediğiniz menü sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="4d672-106">Left-click the menu that you want to copy and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="4d672-107">Sonra amaçlanan yeni konum üst düzey menü sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce üst düzey menü öğesini sağ tıklatın **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="4d672-107">Left-click the top-level menu that is after the intended new location and press CTRL+V, or right-click the top-level menu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="4d672-108">Seçilen üst düzey menü önce kopyaladığınız menüsünün eklenir.</span><span class="sxs-lookup"><span data-stu-id="4d672-108">The menu that you copied is inserted before the selected top-level menu.</span></span>  
  
### <a name="to-copy-a-top-level-menu-and-its-submenu-items-to-a-drop-down-location"></a><span data-ttu-id="4d672-109">Üst düzey menü ve onun alt öğelerini bir açılan konumuna kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="4d672-109">To copy a top-level menu and its submenu items to a drop-down location</span></span>  
  
1.  <span data-ttu-id="4d672-110">Taşıma ve CTRL + C tuşlarına basın veya menü sağ tıklayıp istediğiniz menü sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="4d672-110">Left-click the menu that you want to move and press CTRL+C, or right-click the menu and select **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="4d672-111">Hedef üst düzey menü amaçlanan yeni konumda alt öğe sol ve CTRL + V tuşlarına basın veya seçin ve istenen yeni konumunu olan bir alt öğeye sağ **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="4d672-111">In the destination top-level menu, left-click the submenu item that is above the intended new location and press CTRL+V, or right-click the submenu item that is above the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="4d672-112">Seçilen alt öğeden önce kopyaladığınız menüsünün eklenir.</span><span class="sxs-lookup"><span data-stu-id="4d672-112">The menu that you copied is inserted before the selected submenu item.</span></span>  
  
### <a name="to-copy-a-submenu-item-to-another-menu"></a><span data-ttu-id="4d672-113">Başka bir menüye alt menü öğesini kopyalamak için</span><span class="sxs-lookup"><span data-stu-id="4d672-113">To copy a submenu item to another menu</span></span>  
  
1.  <span data-ttu-id="4d672-114">Kopyala ve CTRL + C tuşlarına basın veya alt öğeye sağ tıklayın ve istediğiniz alt öğesi sol **kopyalama** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="4d672-114">Left-click the submenu item that you want to copy and press CTRL+C, or right-click the submenu item and choose **Copy** from the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="4d672-115">Kesme alt öğe içeren menüsünü tıklatın.</span><span class="sxs-lookup"><span data-stu-id="4d672-115">Left-click the menu that will contain the submenu item that you cut.</span></span>  
  
3.  <span data-ttu-id="4d672-116">Hedeflenen yeni konum önce alt öğeyi sol ve CTRL + V tuşlarına basın veya hedeflenen yeni konum ve select önce alt öğeye sağ tıklayın **Yapıştır** kısayol menüsünden.</span><span class="sxs-lookup"><span data-stu-id="4d672-116">Left-click the submenu item that is before the intended new location and press CTRL+V, or right-click the submenu item that is before the intended new location and select **Paste** from the shortcut menu.</span></span>  
  
     <span data-ttu-id="4d672-117">Seçilen alt öğeden önce kopyaladığınız alt öğe eklenir.</span><span class="sxs-lookup"><span data-stu-id="4d672-117">The submenu item that you copied is inserted before the selected submenu item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d672-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4d672-118">See also</span></span>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- [<span data-ttu-id="4d672-119">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="4d672-119">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
