---
title: MainMenu Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745119"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="c1cb6-102">MainMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c1cb6-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="c1cb6-103"><xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="c1cb6-104">Windows Forms <xref:System.Windows.Forms.MainMenu> bileşeni çalışma zamanında bir menü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="c1cb6-105">Ana menünün ve tek tek öğelerin tüm alt menüleri <xref:System.Windows.Forms.MenuItem> nesneleridir.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="c1cb6-106">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="c1cb6-106">Key Properties</span></span>  
 <span data-ttu-id="c1cb6-107">Bir menü öğesi, <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> özelliği `true`olarak ayarlanarak varsayılan öğe olarak belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="c1cb6-108">Menü tıklandığında varsayılan öğe kalın metinde görünür.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="c1cb6-109">Menü öğesinin <xref:System.Windows.Forms.MenuItem.Checked%2A> özelliği `true` veya `false`ve menü öğesinin seçili olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="c1cb6-110">Menü öğesinin <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> özelliği seçili öğenin görünümünü özelleştirir: <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> `true`olarak ayarlandıysa, öğenin yanında bir radyo düğmesi görünür; <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> `false`olarak ayarlanırsa, öğenin yanında bir onay işareti görünür.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1cb6-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1cb6-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="c1cb6-112">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c1cb6-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
