---
title: MainMenu Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 6c2c33c8c03751e87d71e65523b82d92b18f31c4
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57709889"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="879e7-102">MainMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="879e7-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="879e7-103">Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimleri önceki sürümlerinin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="879e7-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="879e7-104">Windows Forms <xref:System.Windows.Forms.MainMenu> bileşen çalışma zamanında bir menü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="879e7-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="879e7-105">Tek tek öğeleri ana menü ve tüm alt menülerin olan <xref:System.Windows.Forms.MenuItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="879e7-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="879e7-106">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="879e7-106">Key Properties</span></span>  
 <span data-ttu-id="879e7-107">Bir menü öğesini ayarlayarak varsayılan öğesi olarak belirlenebilir <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="879e7-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="879e7-108">Menü tıklandığında varsayılan öğe kalın metin olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="879e7-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="879e7-109">Menü öğesinin <xref:System.Windows.Forms.MenuItem.Checked%2A> özelliği olduğu ya da `true` veya `false`ve menü öğesinin seçili olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="879e7-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="879e7-110">Menü öğesinin <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> özelliği özelleştirir seçili öğenin görünüşünü: varsa <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ayarlanır `true`, varsa öğenin yanında; bir radyo düğmesi görünür <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ayarlanır `false`, öğesinin yanında bir onay işareti görünür.</span><span class="sxs-lookup"><span data-stu-id="879e7-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="879e7-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="879e7-111">See also</span></span>
- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="879e7-112">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="879e7-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
