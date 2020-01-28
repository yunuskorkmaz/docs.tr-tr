---
title: MainMenu Bileşenine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- MenuItem
- MainMenu
helpviewer_keywords:
- MainMenu control [Windows Forms], about MainMenu control
- menus
ms.assetid: b41cc5a3-cc59-4996-aa3c-8dd9c17d3c90
ms.openlocfilehash: 8bc35de239429214d6b493b343d1dd6c898f4d37
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745119"
---
# <a name="mainmenu-component-overview-windows-forms"></a>MainMenu Bileşenine Genel Bakış (Windows Forms)
> [!IMPORTANT]
> <xref:System.Windows.Forms.MenuStrip> ve <xref:System.Windows.Forms.ContextMenuStrip> önceki sürümlerin <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu> denetimlerine işlev ekleyip ekler ve bu, <xref:System.Windows.Forms.MainMenu> ve <xref:System.Windows.Forms.ContextMenu>, hem geri uyumluluk hem de daha ileride kullanılmak üzere korunur.  
  
 Windows Forms <xref:System.Windows.Forms.MainMenu> bileşeni çalışma zamanında bir menü görüntüler. Ana menünün ve tek tek öğelerin tüm alt menüleri <xref:System.Windows.Forms.MenuItem> nesneleridir.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Bir menü öğesi, <xref:System.Windows.Forms.MenuItem.DefaultItem%2A> özelliği `true`olarak ayarlanarak varsayılan öğe olarak belirlenebilir. Menü tıklandığında varsayılan öğe kalın metinde görünür. Menü öğesinin <xref:System.Windows.Forms.MenuItem.Checked%2A> özelliği `true` veya `false`ve menü öğesinin seçili olup olmadığını gösterir. Menü öğesinin <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> özelliği seçili öğenin görünümünü özelleştirir: <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> `true`olarak ayarlandıysa, öğenin yanında bir radyo düğmesi görünür; <xref:System.Windows.Forms.MenuItem.RadioCheck%2A> `false`olarak ayarlanırsa, öğenin yanında bir onay işareti görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.MainMenu>
- <xref:System.Windows.Forms.Menu>
- <xref:System.Windows.Forms.MenuItem>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- [MenuStrip Denetimine Genel Bakış](menustrip-control-overview-windows-forms.md)
