---
title: "ContextMenuStrip Denetimine Genel Bakış"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: ContextMenuStrip
helpviewer_keywords:
- context menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- shortcut menus [Windows Forms], ContextMenuStrip control [Windows Forms]
- ContextMenuStrip control [Windows Forms], about ContextMenuStrip control
ms.assetid: 9787cdb3-88f1-4198-972f-eefd9524ce39
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c04e8095d84468ee7574b31f0a30fb6f2d2b03a0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="contextmenustrip-control-overview"></a><span data-ttu-id="dda8e-102">ContextMenuStrip Denetimine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dda8e-102">ContextMenuStrip Control Overview</span></span>
> [!NOTE]
>  <span data-ttu-id="dda8e-103"><xref:System.Windows.Forms.ContextMenuStrip> Denetimi değiştirir ve işlevlerini ekler <xref:System.Windows.Forms.ContextMenu> kontrol; ancak, <xref:System.Windows.Forms.ContextMenu> denetim tutulur geriye dönük uyumluluk ve gelecekte kullanım için seçerseniz.</span><span class="sxs-lookup"><span data-stu-id="dda8e-103">The <xref:System.Windows.Forms.ContextMenuStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ContextMenu> control; however, the <xref:System.Windows.Forms.ContextMenu> control is retained for backward compatibility and future use if you choose.</span></span>  
  
 <span data-ttu-id="dda8e-104">Kullanıcı farenin sağ düğmesiyle tıklattığında kısayol menüleri, bağlam menülerini olarak da bilinir fare konumunda görünür.</span><span class="sxs-lookup"><span data-stu-id="dda8e-104">Shortcut menus, also called context menus, appear at the mouse position when the user clicks the right mouse button.</span></span> <span data-ttu-id="dda8e-105">Kısayol *menüleri* istemci alanını veya fare işaretçisini konumda denetim için seçenekler sağlar.</span><span class="sxs-lookup"><span data-stu-id="dda8e-105">Shortcut *menus* provide options for the client area or the control at the mouse pointer location.</span></span>  
  
 <span data-ttu-id="dda8e-106"><xref:System.Windows.Forms.ContextMenuStrip> Denetim sorunsuz bir şekilde yeni ile çalışacak şekilde tasarlanmıştır <xref:System.Windows.Forms.ToolStrip> ve ilişkili denetimler, ancak ilişkilendirebilirsiniz bir <xref:System.Windows.Forms.ContextMenuStrip> gibi kolayca diğer denetimleri ile.</span><span class="sxs-lookup"><span data-stu-id="dda8e-106">The <xref:System.Windows.Forms.ContextMenuStrip> control is designed to work seamlessly with the new <xref:System.Windows.Forms.ToolStrip> and related controls, but you can associate a <xref:System.Windows.Forms.ContextMenuStrip> with other controls just as easily.</span></span>  
  
 <span data-ttu-id="dda8e-107">Aşağıdaki tabloda önemli gösterilmektedir <xref:System.Windows.Forms.ContextMenuStrip> Yahoo! companion sınıfları.</span><span class="sxs-lookup"><span data-stu-id="dda8e-107">The following table shows the important <xref:System.Windows.Forms.ContextMenuStrip> companion classes.</span></span>  
  
|<span data-ttu-id="dda8e-108">örneği</span><span class="sxs-lookup"><span data-stu-id="dda8e-108">Class</span></span>|<span data-ttu-id="dda8e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="dda8e-109">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|<span data-ttu-id="dda8e-110">Görüntülenen seçilebilir bir seçeneği temsil eden bir <xref:System.Windows.Forms.MenuStrip> veya <xref:System.Windows.Forms.ContextMenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="dda8e-110">Represents a selectable option displayed on a <xref:System.Windows.Forms.MenuStrip> or <xref:System.Windows.Forms.ContextMenuStrip>.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDown>|<span data-ttu-id="dda8e-111">Kullanıcının kullanıcı tıklattığında görüntülenen bir listeden tek bir öğe seçin olanak tanıyan bir denetimi temsil eden bir <xref:System.Windows.Forms.ToolStripDropDownButton> ya da daha üst düzey menü öğesi.</span><span class="sxs-lookup"><span data-stu-id="dda8e-111">Represents a control that enables the user to select a single item from a list that is displayed when the user clicks a <xref:System.Windows.Forms.ToolStripDropDownButton> or a higher-level menu item.</span></span>|  
|<xref:System.Windows.Forms.ToolStripDropDownItem>|<span data-ttu-id="dda8e-112">Türetilen denetimler için temel işlevleri sağlar <xref:System.Windows.Forms.ToolStripItem> tıklatıldığında açılan öğeleri görüntüleyin.</span><span class="sxs-lookup"><span data-stu-id="dda8e-112">Provides basic functionality for controls derived from <xref:System.Windows.Forms.ToolStripItem> that display drop-down items when clicked.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dda8e-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="dda8e-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDown>
