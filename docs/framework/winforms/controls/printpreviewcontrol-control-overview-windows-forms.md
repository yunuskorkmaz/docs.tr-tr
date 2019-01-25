---
title: PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: acf21365d2694cdc1bf2213187fb2ae047205c4c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665387"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> görüntülemek için kullanılan bir [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırıldığında görünecek. Bu nedenle genellikle kullandığınız hiç düğme yok veya diğer kullanıcı arabirimi öğeleri bu denetime sahiptir <xref:System.Windows.Forms.PrintPreviewControl> yalnızca kendi Yazdır-Önizle kullanıcı arabirimi yazmak istiyorsanız. Standart kullanıcı arabirimi istiyorsanız kullanmak bir <xref:System.Windows.Forms.PrintPreviewDialog> denetimi; bkz [PrintPreviewDialog denetimine genel bakış](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) genel bakış.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, belgenin önizlemesi için ayarlar. Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesne. Belge yazdırma için oluşturma genel bakış için bkz: [PrintDocument bileşenine genel bakış](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) ve [Windows Forms yazdırma desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> Ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özellikleri denetimde yatay ve dikey olarak görüntülenen sayfa sayısını belirler. Daha sorunsuz yükseltmelere görünen metin düzgünleştirme yapabilirsiniz, ancak daha yavaş görünen yapabilirsiniz; Bunu kullanmak için ayarlanmış <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> özelliğini `true`.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl Denetimi](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)
- [İletişim Kutusu Denetimleri ve Bileşenleri](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
