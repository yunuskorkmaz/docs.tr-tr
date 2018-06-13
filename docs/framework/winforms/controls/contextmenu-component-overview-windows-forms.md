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
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu Bileşenine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> önceki sürümlerinin denetimleri <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.  
  
 Windows Forms ile <xref:System.Windows.Forms.ContextMenu> bileşeni, kolayca erişilebilir kısayol menüsü seçili nesne ile ilişkili sık kullanılan komutlar olan kullanıcıların sağlayabilir. Bir kısayol menüsü öğelerini sık başka bir uygulamada görünmesini ana menü öğelerinden bir alt kümesidir. Bir kullanıcı, fareyi sağ tıklayarak bir kısayol menüsü genellikle erişebilir. Windows formlarında kısayol menüleri denetimleri ile ilişkilendirilmiş.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin ayarlayarak bir kısayol menü denetimi ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğine <xref:System.Windows.Forms.ContextMenu> bileşeni. Tek kısayol menüsü birden çok denetimleriyle ilişkili olabilir, ancak her denetim yalnızca bir kısayol menüsü olabilir.  
  
 Anahtar özelliği <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.Menu.MenuItems%2A> özelliği. Menü öğeleri program aracılığıyla oluşturarak ekleyebileceğiniz <xref:System.Windows.Forms.MenuItem> nesneleri ve bunlara ekleme <xref:System.Windows.Forms.Menu.MenuItemCollection> kısayol menüsünün. Bir kısayol menü öğeleri genellikle diğer menülerden çizilir çünkü kopyalayarak en sık bir kısayol menüsü öğelerini ekleyeceksiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.ContextMenu>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>
