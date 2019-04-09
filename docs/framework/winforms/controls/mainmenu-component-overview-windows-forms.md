---
title: MainMenu Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: da1b76a7019f364e7463a8345aa80d9a9bd6089e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168486"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu Bileşenine Genel Bakış (Windows Forms)
> [!IMPORTANT]
>  Ancak <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> değiştirin ve işlevsellik eklemek <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimleri önceki sürümlerinin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> seçerseniz geriye dönük uyumluluk ve gelecekte kullanım için korunur.  
  
 Windows Forms <xref:System.Windows.Forms.MainMenu> bileşen çalışma zamanında bir menü görüntüler. Tek tek öğeleri ana menü ve tüm alt menülerin olan <xref:System.Windows.Forms.MenuItem> nesneleri.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Bir menü öğesini ayarlayarak varsayılan öğesi olarak belirlenebilir <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> özelliğini `true`. Menü tıklandığında varsayılan öğe kalın metin olarak görünür. Menü öğesinin <xref:System.Windows.Forms.MenuItem.Checked%2A> özelliği olduğu ya da `true` veya `false`ve menü öğesinin seçili olup olmadığını gösterir. Menü öğesinin <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> özelliği özelleştirir seçili öğenin görünüşünü: varsa <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ayarlanır `true`, varsa öğenin yanında; bir radyo düğmesi görünür <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> ayarlanır `false`, öğesinin yanında bir onay işareti görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
