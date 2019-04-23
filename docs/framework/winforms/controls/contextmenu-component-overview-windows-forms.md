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
ms.openlocfilehash: 2acbcc9197a630a993471c22e572a4f3ed682c64
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975149"
---
# <a name="contextmenu-component-overview-windows-forms"></a>ContextMenu Bileşenine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimleri önceki sürümlerinin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.  
  
 Windows Forms ile <xref:System.Windows.Forms.ContextMenu> bileşeni ile bir kolayca erişilebilir kısayol menüsünde seçilen bir nesneyle ilişkili sık kullanılan komutlar, kullanıcıların sağlayabilir. Bir kısayol menü öğelerinde, sık sık başka bir uygulamada görüntülenen ana menü öğelerinden bir alt kümesidir. Bir kullanıcı, fare sağ tıklayarak bir kısayol menüsünü genellikle erişebilir. Windows Forms'ta kısayol menüleri denetimleri ile ilişkilendirilir.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin ayarlayarak bir kısayol menü denetimi ile ilişkilendirebilirsiniz <xref:System.Windows.Forms.Control.ContextMenu%2A> özelliğini <xref:System.Windows.Forms.ContextMenu> bileşeni. Tek bir kısayol menüsü birden çok denetim ile ilişkili olabilir ancak her denetim, yalnızca bir kısayol menüsünü olabilir.  
  
 Anahtar özelliği <xref:System.Windows.Forms.ContextMenu> bileşeni <xref:System.Windows.Forms.Menu.MenuItems%2A> özelliği. Menü öğelerini program aracılığıyla oluşturarak ekleyebileceğiniz <xref:System.Windows.Forms.MenuItem> nesneleri ve bunlara ekleme <xref:System.Windows.Forms.Menu.MenuItemCollection> kısayol menüsünün. Bir kısayol menü öğeleri genellikle diğer menülerden çizilir olduğundan, bir kısayol menüsüne kopyalayarak öğeleri sık ekleyeceksiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.ContextMenu>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
