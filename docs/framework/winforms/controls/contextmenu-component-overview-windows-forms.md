---
title: ContextMenu Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- ContextMenu
helpviewer_keywords:
- ContextMenu component [Windows Forms], about ContextMenu component
- context menus [Windows Forms], ContextMenu component
- shortcut menus [Windows Forms], ContextMenu component
ms.assetid: 49d6398f-d3c4-4679-84fa-1de07b68b05e
ms.openlocfilehash: 6ae7817bc158f30fbf55b5f6228ecdf134d6657d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962181"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="c9b16-102">ContextMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="c9b16-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
> <span data-ttu-id="c9b16-103"><xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> , Ve '<xref:System.Windows.Forms.ContextMenuStrip> i önceki sürümlerin ve denetimlerine değiştirebilir ve bunları değiştirip, ve ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. <xref:System.Windows.Forms.MenuStrip></span><span class="sxs-lookup"><span data-stu-id="c9b16-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="c9b16-104">Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeniyle, kullanıcılara, seçilen nesneyle ilişkili sık kullanılan komutların kolay erişilebilir kısayol menüsünü sağlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9b16-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="c9b16-105">Kısayol menüsündeki öğeler genellikle, ana menülerden uygulamanın başka bir yerinde görünen öğelerin bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="c9b16-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="c9b16-106">Kullanıcı, genellikle fareyle sağ tıklanarak bir kısayol menüsüne erişebilir.</span><span class="sxs-lookup"><span data-stu-id="c9b16-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="c9b16-107">Windows Forms, kısayol menüleri denetimlerle ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="c9b16-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="c9b16-108">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="c9b16-108">Key Properties</span></span>  
 <span data-ttu-id="c9b16-109">Denetimin <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.ContextMenu> bileşen olarak ayarlayarak kısayol menüsünü bir denetimle ilişkilendirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9b16-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="c9b16-110">Tek bir kısayol menüsü birden çok denetimle ilişkilendirilebilir, ancak her denetimde yalnızca bir kısayol menüsü olabilir.</span><span class="sxs-lookup"><span data-stu-id="c9b16-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="c9b16-111"><xref:System.Windows.Forms.ContextMenu> Bileşenin<xref:System.Windows.Forms.Menu.MenuItems%2A> anahtar özelliği özelliğidir.</span><span class="sxs-lookup"><span data-stu-id="c9b16-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="c9b16-112">Program aracılığıyla nesne oluşturup <xref:System.Windows.Forms.MenuItem> kısayol menüsüne ekleyerek <xref:System.Windows.Forms.Menu.MenuItemCollection> menü öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9b16-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="c9b16-113">Bir kısayol menüsündeki öğeler genellikle diğer menülerden çizilmediği için, bir kısayol menüsüne en sık bir öğe kopyalayarak öğeleri ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="c9b16-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b16-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c9b16-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
