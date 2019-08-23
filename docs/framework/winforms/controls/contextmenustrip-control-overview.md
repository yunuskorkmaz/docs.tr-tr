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
ms.openlocfilehash: e4a6add5297ba7db606ca1891e9279141f8d6d20
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962151"
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="d81d0-102">ContextMenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d81d0-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
> <span data-ttu-id="d81d0-103">Denetim yerini alır ve <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.ContextMenu> denetime işlevsellik ekler; ancak, denetim geriye dönük uyumluluk için ve isterseniz daha sonra kullanılmak üzere tutulur. <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="d81d0-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="d81d0-104">Bağlam menüleri olarak da adlandırılan kısayol menüleri, Kullanıcı farenin sağ düğmesine tıkladığında fare konumunda görünür.</span><span class="sxs-lookup"><span data-stu-id="d81d0-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="d81d0-105">Kısayol *menüleri* , istemci alanı veya fare işaretçisi konumundaki denetim için seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d81d0-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="d81d0-106">Denetim, yeni <xref:System.Windows.Forms.ToolStrip> ve ilgili denetimlerle sorunsuz bir <xref:System.Windows.Forms.ContextMenuStrip> şekilde çalışacak şekilde tasarlanmıştır, ancak diğer denetimlerle tıpkı kolayca de ilişkilendirebilirsiniz. <xref:System.Windows.Forms.ContextMenuStrip></span><span class="sxs-lookup"><span data-stu-id="d81d0-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="d81d0-107">Aşağıdaki tabloda, önemli <xref:System.Windows.Forms.ContextMenuStrip> yardımcı sınıflar gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="d81d0-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="d81d0-108">örneği</span><span class="sxs-lookup"><span data-stu-id="d81d0-108">Class</span></span>|<span data-ttu-id="d81d0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d81d0-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="d81d0-110"><xref:System.Windows.Forms.MenuStrip> Veya<xref:System.Windows.Forms.ContextMenuStrip>üzerinde görünen seçilebilir bir seçeneği temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d81d0-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="d81d0-111">Kullanıcının bir <xref:System.Windows.Forms.ToolStripDropDownButton> veya daha yüksek düzey menü öğesine tıkladığı zaman görüntülenen listeden tek bir öğe seçmesini sağlayan bir denetimi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d81d0-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="d81d0-112">Tıklandığında <xref:System.Windows.Forms.ToolStripItem> , açılan öğeden türetilmiş denetimler için temel işlevleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="d81d0-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d81d0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d81d0-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDown>
