---
title: ContextMenuStrip Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
ms.openlocfilehash: 23699c67de616ba3f535d2527a315aebe7448d3f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215826"
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="c6c23-102">ContextMenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c6c23-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="c6c23-103"><xref:System.Windows.Forms.ContextMenuStrip> Denetimi değiştirir ve işlevsellik ekler <xref:System.Windows.Forms.ContextMenu> denetler; ancak, <xref:System.Windows.Forms.ContextMenu> denetim korunur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="c6c23-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="c6c23-104">Kullanıcının sağ fare düğmesine tıkladığında fare konumundan bağlam menüleri olarak da bilinen kısayol menülerini görünür.</span><span class="sxs-lookup"><span data-stu-id="c6c23-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="c6c23-105">Kısayol *menüleri* istemci alanını veya fare işaretçisi konumunu denetim için seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c6c23-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="c6c23-106"><xref:System.Windows.Forms.ContextMenuStrip> Denetimi, sorunsuz bir şekilde yeni ile çalışacak şekilde tasarlanmıştır <xref:System.Windows.Forms.ToolStrip> ve ilgili denetimleri, ancak ilişkilendirebilir bir <xref:System.Windows.Forms.ContextMenuStrip> gibi kolayca diğer denetimlerle.</span><span class="sxs-lookup"><span data-stu-id="c6c23-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="c6c23-107">Aşağıdaki tablo önemli gösterir <xref:System.Windows.Forms.ContextMenuStrip> Yahoo! companion sınıfları.</span><span class="sxs-lookup"><span data-stu-id="c6c23-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="c6c23-108">örneği</span><span class="sxs-lookup"><span data-stu-id="c6c23-108">Class</span></span>|<span data-ttu-id="c6c23-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c6c23-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="c6c23-110">Görüntülenen bir seçilebilir seçeneğini temsil eder bir <xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="c6c23-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="c6c23-111">Kullanıcının kullanıcı tıkladığında görüntülenen listeden tek bir öğe seçmesini sağlayan bir denetimi temsil eder bir <xref:System.Windows.Forms.ToolStripDropDownButton> ya da daha üst düzey menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="c6c23-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="c6c23-112">Türetilen denetimler için temel işlevleri sağlar <xref:System.Windows.Forms.ToolStripItem> tıklandığında açılan öğeleri görüntüler.</span><span class="sxs-lookup"><span data-stu-id="c6c23-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c6c23-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c6c23-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
