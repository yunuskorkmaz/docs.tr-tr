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
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu Bileşenine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> <xref:System.Windows.Forms.MainMenu> <xref:System.Windows.Forms.ContextMenu> , Ve '<xref:System.Windows.Forms.ContextMenuStrip> i önceki sürümlerin ve denetimlerine değiştirebilir ve bunları değiştirip, ve ' ı seçerseniz hem geri uyumluluk hem de gelecekte kullanılmak üzere korunur. <xref:System.Windows.Forms.MenuStrip>  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeniyle, kullanıcılara, seçilen nesneyle ilişkili sık kullanılan komutların kolay erişilebilir kısayol menüsünü sağlayabilirsiniz. Kısayol menüsündeki öğeler genellikle, ana menülerden uygulamanın başka bir yerinde görünen öğelerin bir alt kümesidir. Kullanıcı, genellikle fareyle sağ tıklanarak bir kısayol menüsüne erişebilir. Windows Forms, kısayol menüleri denetimlerle ilişkilendirilir.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.ContextMenu> bileşen olarak ayarlayarak kısayol menüsünü bir denetimle ilişkilendirebilirsiniz. Tek bir kısayol menüsü birden çok denetimle ilişkilendirilebilir, ancak her denetimde yalnızca bir kısayol menüsü olabilir.  
  
 <xref:System.Windows.Forms.ContextMenu> Bileşenin<xref:System.Windows.Forms.Menu.MenuItems%2A> anahtar özelliği özelliğidir. Program aracılığıyla nesne oluşturup <xref:System.Windows.Forms.MenuItem> kısayol menüsüne ekleyerek <xref:System.Windows.Forms.Menu.MenuItemCollection> menü öğeleri ekleyebilirsiniz. Bir kısayol menüsündeki öğeler genellikle diğer menülerden çizilmediği için, bir kısayol menüsüne en sık bir öğe kopyalayarak öğeleri ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
