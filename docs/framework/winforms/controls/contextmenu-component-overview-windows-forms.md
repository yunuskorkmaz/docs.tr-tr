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
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu Bileşenine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.  
  
 Windows Forms <xref:System.Windows.Forms.ContextMenu> bileşeniyle, kullanıcılara, seçilen nesneyle ilişkili sık kullanılan komutların kolay erişilebilir kısayol menüsünü sağlayabilirsiniz. Kısayol menüsündeki öğeler genellikle, ana menülerden uygulamanın başka bir yerinde görünen öğelerin bir alt kümesidir. Kullanıcı, genellikle fareyle sağ tıklanarak bir kısayol menüsüne erişebilir. Windows Forms, kısayol menüleri denetimlerle ilişkilendirilir.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.ContextMenu> bileşeni olarak ayarlayarak kısayol menüsünü bir denetimle ilişkilendirebilirsiniz. Tek bir kısayol menüsü birden çok denetimle ilişkilendirilebilir, ancak her denetimde yalnızca bir kısayol menüsü olabilir.  
  
 <xref:System.Windows.Forms.ContextMenu> bileşenin anahtar özelliği <xref:System.Windows.Forms.Menu.MenuItems%2A> özelliğidir. Program aracılığıyla <xref:System.Windows.Forms.MenuItem> nesne oluşturup kısayol menüsünün <xref:System.Windows.Forms.Menu.MenuItemCollection> ekleyerek menü öğeleri ekleyebilirsiniz. Bir kısayol menüsündeki öğeler genellikle diğer menülerden çizilmediği için, bir kısayol menüsüne en sık bir öğe kopyalayarak öğeleri ekleyebilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
