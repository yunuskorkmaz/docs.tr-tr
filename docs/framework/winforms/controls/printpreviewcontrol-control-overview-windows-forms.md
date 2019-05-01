---
title: PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
ms.openlocfilehash: e9f1c2ae912b6beeba70c318b94a3052e2f99acb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62012608"
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> görüntülemek için kullanılan bir [PrintDocument](printdocument-component-windows-forms.md) yazdırıldığında görünecek. Bu nedenle genellikle kullandığınız hiç düğme yok veya diğer kullanıcı arabirimi öğeleri bu denetime sahiptir <xref:System.Windows.Forms.PrintPreviewControl> yalnızca kendi Yazdır-Önizle kullanıcı arabirimi yazmak istiyorsanız. Standart kullanıcı arabirimi istiyorsanız kullanmak bir <xref:System.Windows.Forms.PrintPreviewDialog> denetimi; bkz [PrintPreviewDialog denetimine genel bakış](printpreviewdialog-control-overview-windows-forms.md) genel bakış.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, belgenin önizlemesi için ayarlar. Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesne. Belge yazdırma için oluşturma genel bakış için bkz: [PrintDocument bileşenine genel bakış](printdocument-component-overview-windows-forms.md) ve [Windows Forms yazdırma desteği](../advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> Ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özellikleri denetimde yatay ve dikey olarak görüntülenen sayfa sayısını belirler. Daha sorunsuz yükseltmelere görünen metin düzgünleştirme yapabilirsiniz, ancak daha yavaş görünen yapabilirsiniz; Bunu kullanmak için ayarlanmış <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> özelliğini `true`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Forms.PrintPreviewControl>
- [PrintPreviewDialog Denetimine Genel Bakış](printpreviewdialog-control-overview-windows-forms.md)
- [PrintPreviewControl Denetimi](printpreviewcontrol-control-windows-forms.md)
- [İletişim Kutusu Denetimleri ve Bileşenleri](dialog-box-controls-and-components-windows-forms.md)
