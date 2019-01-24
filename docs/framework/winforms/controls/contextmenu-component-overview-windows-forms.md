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
ms.openlocfilehash: 7da0522dae00608ead356484a31d219a67ec4ba9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545679"
---
# <a name="contextmenu-component-overview-windows-forms"></a><span data-ttu-id="1c9c0-102">ContextMenu Bileşenine Genel Bakış (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1c9c0-102">ContextMenu Component Overview (Windows Forms)</span></span>
> [!IMPORTANT]
>  <span data-ttu-id="1c9c0-103">Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimleri önceki sürümlerinin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-103">Although <xref:System.Windows.Forms.MenuStrip> and <xref:System.Windows.Forms.ContextMenuStrip> replace and add functionality to the <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> controls of previous versions, <xref:System.Windows.Forms.MainMenu> and <xref:System.Windows.Forms.ContextMenu> are retained for both backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="1c9c0-104">Windows Forms ile <xref:System.Windows.Forms.ContextMenu> bileşeni ile bir kolayca erişilebilir kısayol menüsünde seçilen bir nesneyle ilişkili sık kullanılan komutlar, kullanıcıların sağlayabilir.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-104">With the Windows Forms <xref:System.Windows.Forms.ContextMenu> component, you can provide users with an easily accessible shortcut menu of frequently used commands that are associated with the selected object.</span></span> <span data-ttu-id="1c9c0-105">Bir kısayol menü öğelerinde, sık sık başka bir uygulamada görüntülenen ana menü öğelerinden bir alt kümesidir.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-105">The items in a shortcut menu are frequently a subset of the items from main menus that appear elsewhere in the application.</span></span> <span data-ttu-id="1c9c0-106">Bir kullanıcı, fare sağ tıklayarak bir kısayol menüsünü genellikle erişebilir.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-106">A user can typically access a shortcut menu by right-clicking the mouse.</span></span> <span data-ttu-id="1c9c0-107">Windows Forms'ta kısayol menüleri denetimleri ile ilişkilendirilir.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-107">On Windows Forms, shortcut menus are associated with controls.</span></span>  
  
## <a name="key-properties"></a><span data-ttu-id="1c9c0-108">Anahtar Özellikler</span><span class="sxs-lookup"><span data-stu-id="1c9c0-108">Key Properties</span></span>  
 <span data-ttu-id="1c9c0-109">Denetimin ayarlayarak bir kısayol menü denetimi ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.ContextMenu> bileşeni.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-109">You can associate a shortcut menu with a control by setting the control's <xref:System.Windows.Forms.Control.ContextMenu%2A> property to the <xref:System.Windows.Forms.ContextMenu> component.</span></span> <span data-ttu-id="1c9c0-110">Tek bir kısayol menüsü birden çok denetim ile ilişkili olabilir ancak her denetim, yalnızca bir kısayol menüsünü olabilir.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-110">A single shortcut menu can be associated with multiple controls, but each control can have only one shortcut menu.</span></span>  
  
 <span data-ttu-id="1c9c0-111">Anahtar özelliği <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.Menu.MenuItems%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-111">The key property of the <xref:System.Windows.Forms.ContextMenu> component is the <xref:System.Windows.Forms.Menu.MenuItems%2A> property.</span></span> <span data-ttu-id="1c9c0-112">Menü öğelerini program aracılığıyla oluşturarak ekleyebileceğiniz <xref:System.Windows.Forms.MenuItem> nesneleri ve bunlara ekleme <xref:System.Windows.Forms.Menu.MenuItemCollection> kısayol menüsünün.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-112">You can add menu items by programmatically creating <xref:System.Windows.Forms.MenuItem> objects and adding them to the <xref:System.Windows.Forms.Menu.MenuItemCollection> of the shortcut menu.</span></span> <span data-ttu-id="1c9c0-113">Bir kısayol menü öğeleri genellikle diğer menülerden çizilir olduğundan, bir kısayol menüsüne kopyalayarak öğeleri sık ekleyeceksiniz.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-113">Because the items in a shortcut menu are usually drawn from other menus, you will most frequently add items to a shortcut menu by copying them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c9c0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c9c0-114">See also</span></span>
- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
