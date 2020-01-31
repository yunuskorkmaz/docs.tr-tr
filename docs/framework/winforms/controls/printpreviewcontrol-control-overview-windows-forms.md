---
title: PrintPreviewControl Denetimine Genel Bakış
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: 8dfe5802a24d5ec85ed908fd04c5550e1fbec012
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741441"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl>, yazdırıldığında görüneceği şekilde bir [PrintDocument](printdocument-component-windows-forms.md) göstermek için kullanılır. Bu denetimde hiçbir düğme veya diğer kullanıcı arabirimi öğesi yoktur, bu nedenle genellikle <xref:System.Windows.Forms.PrintPreviewControl> yalnızca kendi baskı önizleme Kullanıcı arabiriminizi yazmak istiyorsanız kullanırsınız. Standart Kullanıcı arabirimini istiyorsanız, bir <xref:System.Windows.Forms.PrintPreviewDialog> denetimi kullanın; genel bakış için bkz. [Printönizleme Iletişim kutusu denetimine genel bakış](printpreviewdialog-control-overview-windows-forms.md) .  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin anahtar özelliği, belgeyi önizlenen olarak ayarlayan <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>. Belge bir <xref:System.Drawing.Printing.PrintDocument> nesnesi olmalıdır. Yazdırma için belge oluşturmaya genel bakış için bkz. [PrintDocument Bileşenine Genel Bakış](printdocument-component-overview-windows-forms.md) ve [yazdırma desteği Windows Forms](../advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özellikleri, denetimde yatay ve dikey olarak görünen sayfa sayısını belirler. Düzgünleştirme, metnin daha düzgün görünmesine neden olabilir, ancak aynı zamanda görüntüyü daha yavaş hale getirir; kullanmak için <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> özelliğini `true`olarak ayarlayın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog Denetimine Genel Bakış](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl Denetimi](printpreviewcontrol-control-windows-forms.md)
- [İletişim Kutusu Denetimleri ve Bileşenleri](dialog-box-controls-and-components-windows-forms.md)
