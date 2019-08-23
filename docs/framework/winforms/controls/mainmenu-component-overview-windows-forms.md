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
ms.openlocfilehash: fe46683faee13bad951d5a7185aad8a687c290ef
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952128"
---
# <a name="mainmenu-component-overview-windows-forms"></a><span data-ttu-id="ff4c3-102">MainMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ff4c3-102">MainMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="ff4c3-103"><xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> , Ve '<xref:System.Windows.Forms.ContextMenuStrip> i önceki sürümlerin ve denetimlerine değiştirebilir ve bunları değiştirip, ve ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="ff4c3-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="ff4c3-104">Windows Forms <xref:System.Windows.Forms.MainMenu> bileşeni çalışma zamanında bir menü görüntüler.</span><span class="sxs-lookup"><span data-stu-id="ff4c3-104">The Windows Forms <xref:System.Windows.Forms.MainMenu> component displays a menu at run time.</span></span> <span data-ttu-id="ff4c3-105">Ana menünün ve ayrı öğelerin tüm alt menüleri nesnelerdir <xref:System.Windows.Forms.MenuItem> .</span><span class="sxs-lookup"><span data-stu-id="ff4c3-105">All submenus of the main menu and individual items are <xref:System.Windows.Forms.MenuItem> objects.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="ff4c3-106">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="ff4c3-106">Key Properties</span></span>  
 <span data-ttu-id="ff4c3-107">Bir menü öğesi, <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> `true`özelliği olarak ayarlanarak varsayılan öğe olarak belirlenebilir.</span><span class="sxs-lookup"><span data-stu-id="ff4c3-107">A menu item can be designated as the default item by setting the <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> property to `true`.</span></span> <span data-ttu-id="ff4c3-108">Menü tıklandığında varsayılan öğe kalın metinde görünür.</span><span class="sxs-lookup"><span data-stu-id="ff4c3-108">The default item appears in bold text when the menu is clicked.</span></span> <span data-ttu-id="ff4c3-109">Menü öğesinin <xref:System.Windows.Forms.MenuItem.Checked%2A> özelliği ya `true` `false`da olur ve menü öğesinin seçili olup olmadığını gösterir.</span><span class="sxs-lookup"><span data-stu-id="ff4c3-109">The menu item's <xref:System.Windows.Forms.MenuItem.Checked%2A> property is either `true` or `false`, and indicates whether the menu item is selected.</span></span> <span data-ttu-id="ff4c3-110">Menü <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> öğesinin özelliği seçili öğenin görünümünü özelleştirir <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> : olarak `true`ayarlanırsa, öğenin yanında bir radyo <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> düğmesi görünür; olarak `false`ayarlanırsa, öğenin yanında bir onay işareti görünür.</span><span class="sxs-lookup"><span data-stu-id="ff4c3-110">The menu item's <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> property customizes the appearance of the selected item: if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `true`, a radio button appears next to the item; if <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> is set to `false`, a check mark appears next to the item.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff4c3-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff4c3-111">See also</span></span>

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [<span data-ttu-id="ff4c3-112">MenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ff4c3-112">MenuStrip Control Overview</span></span>](menustrip-control-overview-windows-forms.md)
