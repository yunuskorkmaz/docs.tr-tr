---
title: ContextMenu Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 83740221894941d09d1014585513043851a518e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746193"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="7d0c5-102">ContextMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7d0c5-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="7d0c5-103"><xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="7d0c5-104">Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeniyle, kullanıcılara, seçilen nesneyle ilişkili sık kullanılan komutların kolay erişilebilir kısayol menüsünü sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="7d0c5-105">Kısayol menüsündeki öğeler genellikle, ana menülerden uygulamanın başka bir yerinde görünen öğelerin bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="7d0c5-106">Kullanıcı, genellikle fareyle sağ tıklanarak bir kısayol menüsüne erişebilir.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="7d0c5-107">Windows Forms, kısayol menüleri denetimlerle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="7d0c5-108">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="7d0c5-108">Key Properties</span></span>  
 <span data-ttu-id="7d0c5-109">Denetimin <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.ContextMenu> bileşeni olarak ayarlayarak kısayol menüsünü bir denetimle ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="7d0c5-110">Tek bir kısayol menüsü birden çok denetimle ilişkilendirilebilir, ancak her denetimde yalnızca bir kısayol menüsü olabilir.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="7d0c5-111"><xref:System.Windows.Forms.ContextMenu> bileşenin anahtar özelliği <xref:System.Windows.Forms.Menu.MenuItems%2A> özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="7d0c5-112">Program aracılığıyla <xref:System.Windows.Forms.MenuItem> nesne oluşturup kısayol menüsünün <xref:System.Windows.Forms.Menu.MenuItemCollection> ekleyerek menü öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="7d0c5-113">Bir kısayol menüsündeki öğeler genellikle diğer menülerden çizilmediği için, bir kısayol menüsüne en sık bir öğe kopyalayarak öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d0c5-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7d0c5-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
