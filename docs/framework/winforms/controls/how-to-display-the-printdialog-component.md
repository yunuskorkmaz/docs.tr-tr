---
title: "Nasıl yapılır: PrintDialog Bileşenini Görüntüleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7e1162a4e926d5be35f8f7bb7cdeb92264f293aa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-the-printdialog-component"></a>Nasıl yapılır: PrintDialog Bileşenini Görüntüleme
<xref:System.Windows.Forms.PrintDialog> Birçok kullanıcılarınızın aşina olacaktır standart Windows yazdırma iletişim kutusu bir bileşendir. Kullanıcılarınızın rahat hemen olacağından kullanabilmeniz için faydalı olacaktır <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
### <a name="to-display-the-printdialog-component"></a>PrintDialog bileşeni görüntülemek için  
  
-   Çağrı <xref:System.Windows.Forms.Form.ShowDialog%2A> uygulamanızın kodundaki yönteminden.  
  
     Bileşen gösterilen sonra kullanıcılar ile yazdırma işinin özelliklerini ayarlama etkileşim. Bunlar kaydedilir <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` sınıfı (ve <xref:System.Drawing.Printing.PageSettings> kullanıcı erişirse, sınıf [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni), yazdırma işi ile ilişkili. Yazdırma işinin özelliklerini belirlemek ayarlayın çağrıları özellikleri daha sonra yapabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: standart Windows Forms yazdırma işleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Nasıl yapılır: çalışma zamanında bir printdialog'dan kullanıcı girişi yakalama](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [PrintPreviewDialog denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [PrintDialog bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Windows Forms yazdırma desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms denetimleri](../../../../docs/framework/winforms/controls/index.md)
