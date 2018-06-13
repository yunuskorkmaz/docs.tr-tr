---
title: 'Nasıl yapılır: PrintDialog Bileşenini Görüntüleme'
ms.date: 03/30/2017
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], displaying
- printing [Windows Forms], displaying print dialog box
ms.assetid: 745a8db7-0526-4b21-b09d-18e13ed32014
ms.openlocfilehash: d8765187522f8becf24b519434b7c170c1c755b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532193"
---
# <a name="how-to-display-the-printdialog-component"></a>Nasıl yapılır: PrintDialog Bileşenini Görüntüleme
<xref:System.Windows.Forms.PrintDialog> Birçok kullanıcılarınızın aşina olacaktır standart Windows yazdırma iletişim kutusu bir bileşendir. Kullanıcılarınızın rahat hemen olacağından kullanabilmeniz için faydalı olacaktır <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
### <a name="to-display-the-printdialog-component"></a>PrintDialog bileşeni görüntülemek için  
  
-   Çağrı <xref:System.Windows.Forms.Form.ShowDialog%2A> uygulamanızın kodundaki yönteminden.  
  
     Bileşen gösterilen sonra kullanıcılar ile yazdırma işinin özelliklerini ayarlama etkileşim. Bunlar kaydedilir <!--zz <xref:System.Drawing.Printing.PrinterSetting>--> `PrinterSetting` sınıfı (ve <xref:System.Drawing.Printing.PageSettings> kullanıcı erişirse, sınıf [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) aracılığıyla <xref:System.Windows.Forms.PrintDialog> bileşeni), yazdırma işi ile ilişkili. Yazdırma işinin özelliklerini belirlemek ayarlayın çağrıları özellikleri daha sonra yapabilirsiniz.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 [Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 [PrintPreviewDialog Denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [PrintDialog Bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 [Windows Forms Yazdırma Desteği](../../../../docs/framework/winforms/advanced/windows-forms-print-support.md)  
 [Windows Forms Denetimleri](../../../../docs/framework/winforms/controls/index.md)
