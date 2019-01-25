---
title: 'Nasıl yapılır: PrintDialog bileşenini görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: 5315dc8b47c8ca846376ac6d1da5a0bf46fd6241
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54544003"
---
# <a name="how-to-display-the-printdialog-component"></a>Nasıl yapılır: PrintDialog bileşenini görüntüleme
<xref:System.Windows.Forms.PrintDialog> Kullanıcılarınızın birçoğu ile tanıdık gelecektir standart Windows yazdırma iletişim kutusunda bir bileşendir. Kullanıcılarınızın rahat hemen olacağından, kullanabilmeniz için faydalı olacaktır <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
### <a name="to-display-the-printdialog-component"></a>PrintDialog bileşenini görüntüleme için  
  
-   Çağrı <xref:System.Windows.Forms.Form.ShowDialog%2A> uygulamanızın kodundaki yöntemi.  
  
     Bileşen gösterilen sonra kullanıcılar, yazdırma işinin özelliklerini ayarlama etkileşim. Bunlar kaydedilir <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` sınıfı (ve <xref:System.Drawing.Printing.PageSettings> kullanıcı erişirse, sınıf [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni), yazdırma işi ile ilişkili. Daha sonra yazdırma işinin özelliklerini belirlemek için ayarladıkları çağrıları özelliklerine de yapabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)
- [Nasıl yapılır: Kullanıcı girişi bir printdialog'dan çalışma zamanında yakalama](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)
- [PrintPreviewDialog Denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)
- [PrintDialog Bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
- [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)
- [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)
