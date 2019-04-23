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
ms.openlocfilehash: da1b76a7019f364e7463a8345aa80d9a9bd6089e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168486"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="fc213-102">MainMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fc213-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="fc213-103">Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimleri önceki sürümlerinin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="fc213-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="fc213-104">Windows Forms <xref:System.Windows.Forms.MainMenu> bileşen çalışma zamanında bir menü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="fc213-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="fc213-105">Tek tek öğeleri ana menü ve tüm alt menülerin olan <xref:System.Windows.Forms.MenuItem> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="fc213-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="fc213-106">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="fc213-106">Key Properties</span></span>  
 <span data-ttu-id="fc213-107">Bir menü öğesini ayarlayarak varsayılan öğesi olarak belirlenebilir <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="fc213-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="fc213-108">Menü tıklandığında varsayılan öğe kalın metin olarak görünür.</span><span class="sxs-lookup"><span data-stu-id="fc213-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="fc213-109">Menü öğesinin <xref:System.Windows.Forms.MenuItem.Checked%2A> özelliği olduğu ya da `true` veya `false`ve menü öğesinin seçili olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="fc213-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="fc213-110">Menü öğesinin <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> özelliği özelleştirir seçili öğenin görünüşünü: varsa <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ayarlanır `true`, varsa öğenin yanında; bir radyo düğmesi görünür <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ayarlanır `false`, öğesinin yanında bir onay işareti görünür.</span><span class="sxs-lookup"><span data-stu-id="fc213-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc213-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc213-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="fc213-112">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="fc213-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
