---
title: "PrintPreviewControl Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewControl
helpviewer_keywords:
- print preview
- PrintPreviewControl control
ms.assetid: 4513c6c7-5e9b-4f4c-82ca-00f993a26955
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47bef441b01d8bdcf9a365c341005cff28c64f27
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> görüntülemek için kullanılan bir [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırıldığında görüneceği şekilde. Bu denetim yok düğmeler veya diğer kullanıcı arabirimi öğeleri nedenle genellikle kullandığınız sahip <xref:System.Windows.Forms.PrintPreviewControl> yalnızca kendi Baskı Önizleme kullanıcı arabirimini yazmak istiyorsanız. Standart kullanıcı arabirimi istiyorsanız kullanın bir <xref:System.Windows.Forms.PrintPreviewDialog> denetlemek; bkz [PrintPreviewDialog denetimine genel bakış](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) bir genel bakış.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, önizlemesi belgeye ayarlar. Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesnesi. Yazdırma için belgeler oluşturma genel bakış için bkz: [PrintDocument bileşenine genel bakış](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) ve [Windows Forms yazdırma desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> Ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özellikleri, yatay ve dikey olarak denetiminde görüntülenen sayfaların sayısını belirler. Düzgünleştirme metnin sorunsuz görünmesini sağlayabilirsiniz, ancak daha yavaş görüntü yapabilirsiniz; Bunu kullanmak üzere ayarlanmış <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> özelliğine `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [PrintPreviewDialog denetimine genel bakış](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [PrintPreviewControl denetimi](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [İletişim kutusu denetimleri ve bileşenleri](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
