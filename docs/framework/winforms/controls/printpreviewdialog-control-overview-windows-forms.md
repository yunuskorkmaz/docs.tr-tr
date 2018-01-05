---
title: "PrintPreviewDialog Denetimine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: PrintPreviewDialog
helpviewer_keywords: PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed071a4d38a0167ac9414ee7d383736dd38a62a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog Denetimine Genel Bakış (Windows Forms)
Windows Forms <xref:System.Windows.Forms.PrintPreviewDialog> denetimidir görüntülemek için kullanılan bir önceden yapılandırılmış iletişim kutusu nasıl bir [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırıldığında görünür. Kendi iletişim kutusu yapılandırma yerine basit bir çözüm olarak, Windows tabanlı uygulamanızda kullanın. Denetim yazdırma ve yakınlaştırma, bir veya birden çok sayfa görüntüleme ve iletişim kutusunu kapatmak için düğmeler içerir.  
  
## <a name="key-properties-and-methods"></a>Anahtar özellikleri ve yöntemleri  
 Denetimin anahtar özelliği <xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>, önizlemesi belgeye ayarlar. Belge olmalıdır bir <xref:System.Drawing.Printing.PrintDocument> nesnesi. İletişim kutusunu görüntülemek için çağırmalısınız kendi <xref:System.Windows.Forms.Form.ShowDialog%2A> yöntemi. Yumuşatma metnin sorunsuz görünmesini sağlayabilirsiniz, ancak daha yavaş görüntü yapabilirsiniz; Bunu kullanmak üzere ayarlanmış <xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A> özelliğine `true`.  
  
 Belirli özellikleri aracılığıyla kullanılabilir <xref:System.Windows.Forms.PrintPreviewControl> , <xref:System.Windows.Forms.PrintPreviewDialog> içerir. (Bu eklemek zorunda değilsiniz <xref:System.Windows.Forms.PrintPreviewControl> forma; bu otomatik olarak içinde yer <xref:System.Windows.Forms.PrintPreviewDialog> formunuza iletişim eklediğinizde.) Aracılığıyla kullanılabilen özellikleri örnekleri <xref:System.Windows.Forms.PrintPreviewControl> olan <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> ve <xref:System.Windows.Forms.PrintPreviewControl.Rows%2A> yatay ve dikey olarak denetiminde görüntülenen sayfaların sayısını belirlemek özellikleri. Erişebileceğiniz <xref:System.Windows.Forms.PrintPreviewControl.Columns%2A> özelliği olarak `PrintPreviewDialog1.PrintPreviewControl.Columns` içinde [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)], `printPreviewDialog1.PrintPreviewControl.Columns` içinde [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], veya `printPreviewDialog1->PrintPreviewControl->Columns` içinde [!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)].  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [PrintPreviewControl Denetimine Genel Bakış](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [PrintPreviewDialog Denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [İletişim Kutusu Denetimleri ve Bileşenleri](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
