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
ms.workload: dotnet
ms.openlocfilehash: d50e772cf870d47314a25347f4909367062ffb94
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewcontrol-control-overview-windows-forms"></a>PrintPreviewControl Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewControl> görüntülemek için kullanılan bir [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırıldığında görüneceği şekilde. Bu denetim yok düğmeler veya diğer kullanıcı arabirimi öğeleri nedenle genellikle kullandığınız sahip <xref:System.Windows.Forms.PrintPreviewControl> yalnızca kendi Baskı Önizleme kullanıcı arabirimini yazmak istiyorsanız. Standart kullanıcı arabirimi istiyorsanız kullanın bir <xref:System.Windows.Forms.PrintPreviewDialog> denetlemek; bkz [PrintPreviewDialog denetimine genel bakış](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md) bir genel bakış.  
  
## <a name="key-properties"></a>Anahtar Özellikler  
 Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewControl.Document%2A>, önizlemesi belgeye ayarlar. Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesnesi. Yazdırma için belgeler oluşturma genel bakış için bkz: [PrintDocument bileşenine genel bakış](../../../../docs/framework/winforms/controls/printdocument-component-overview-windows-forms.md) ve [Windows Forms yazdırma desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md). <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> Ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> özellikleri, yatay ve dikey olarak denetiminde görüntülenen sayfaların sayısını belirler. Düzgünleştirme metnin sorunsuz görünmesini sağlayabilirsiniz, ancak daha yavaş görüntü yapabilirsiniz; Bunu kullanmak üzere ayarlanmış <xref:System.Windows.Forms.PrintPreviewControl.UseAntiAlias%2A> özelliğine `true`.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.PrintPreviewControl>  
 [PrintPreviewDialog Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/printpreviewdialog-control-overview-windows-forms.md)  
 [PrintPreviewControl Denetimi](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-windows-forms.md)  
 [İletişim Kutusu Denetimleri ve Bileşenleri](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
