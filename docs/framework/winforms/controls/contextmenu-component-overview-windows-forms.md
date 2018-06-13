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
ms.openlocfilehash: 5d548815533e8f9bb37ad00129a5ae526612ea08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526129"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="86411-102">ContextMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="86411-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="86411-103">Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> önceki sürümlerinin denetimleri <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="86411-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="86411-104">Windows Forms ile <xref:System.Windows.Forms.ContextMenu> bileşeni, kolayca erişilebilir kısayol menüsü seçili nesne ile ilişkili sık kullanılan komutlar olan kullanıcıların sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="86411-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="86411-105">Bir kısayol menüsü öğelerini sık başka bir uygulamada görünmesini ana menü öğelerinden bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="86411-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="86411-106">Bir kullanıcı, fareyi sağ tıklayarak bir kısayol menüsü genellikle erişebilir.</span><span class="sxs-lookup"><span data-stu-id="86411-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="86411-107">Windows formlarında kısayol menüleri denetimleri ile ilişkilendirilmiş.</span><span class="sxs-lookup"><span data-stu-id="86411-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="86411-108">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="86411-108">Key Properties</span></span>  
 <span data-ttu-id="86411-109">Denetimin ayarlayarak bir kısayol menü denetimi ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğine <xref:System.Windows.Forms.ContextMenu> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="86411-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="86411-110">Tek kısayol menüsü birden çok denetimleriyle ilişkili olabilir, ancak her denetim yalnızca bir kısayol menüsü olabilir.</span><span class="sxs-lookup"><span data-stu-id="86411-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="86411-111">Anahtar özelliği <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.Menu.MenuItems%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="86411-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="86411-112">Menü öğeleri program aracılığıyla oluşturarak ekleyebileceğiniz <xref:System.Windows.Forms.MenuItem> nesneleri ve bunlara ekleme <xref:System.Windows.Forms.Menu.MenuItemCollection> kısayol menüsünün.</span><span class="sxs-lookup"><span data-stu-id="86411-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="86411-113">Bir kısayol menü öğeleri genellikle diğer menülerden çizilir çünkü kopyalayarak en sık bir kısayol menüsü öğelerini ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="86411-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86411-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="86411-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
