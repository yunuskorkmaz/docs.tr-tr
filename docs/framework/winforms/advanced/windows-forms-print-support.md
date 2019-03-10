---
title: Windows Forms Yazdırma Desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: 8e008f2cb4b2f32cdba676e68d9fd790530e2b06
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708138"
---
# <a name="windows-forms-print-support"></a>Windows Forms Yazdırma Desteği
Windows Forms'ta baskı oluşur öncelikle kullanarak [PrintDocument bileşeni](../controls/printdocument-component-windows-forms.md) yazdırmak, kullanıcının etkinleştirmek için bileşen ve [PrintPreviewDialog denetimi](../controls/printpreviewdialog-control-windows-forms.md) denetimi [PrintDialog Bileşen](../controls/printdialog-component-windows-forms.md) ve [PageSetupDialog bileşeni](../controls/pagesetupdialog-component-windows-forms.md) alışmanızı sağlamak için Windows işletim sistemi kullanıcılara tanıdık bir grafik arabirim sağlamak için bileşenler.  
  
 Genellikle, yeni bir örneğini oluşturduğunuz <xref:System.Drawing.Printing.PrintDocument> bileşeni kullanarak yazdırma gerekenler açıklayan özellikleri ayarlamak <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları ve çağrı <xref:System.Drawing.Printing.PrintDocument.Print%2A> gerçekten belge yazdırma için yöntemi.  
  
 Windows tabanlı bir uygulama yazdırma süresince <xref:System.Drawing.Printing.PrintDocument> bileşeni iptal uyarı kullanıcıların yazdırma oluştuğunu olgu ve yazdırma işinin izin vermek için bir iptal Yazdır iletişim kutusunu gösterir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Standart Windows Forms yazdırma işleri oluşturma](how-to-create-standard-windows-forms-print-jobs.md)  
 Nasıl kullanılacağını açıklar <xref:System.Drawing.Printing.PrintDocument> bir Windows formdan yazdırmak için bileşen.  
  
 [Nasıl yapılır: Kullanıcı girişi bir printdialog'dan çalışma zamanında yakalama](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Program aracılığıyla kullanarak seçilen yazdırma seçeneklerinin nasıl değiştirileceği açıklanmaktadır <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
 [Nasıl yapılır: Windows Forms'ta bir kullanıcının bilgisayarına bağlanan yazıcıları seçme](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Yazıcıyı kullanarak yazdırılacak değiştirmeyi açıklar <xref:System.Windows.Forms.PrintDialog> çalışma zamanında bileşeni.  
  
 [Nasıl yapılır: Windows Forms'ta grafik yazdırma](how-to-print-graphics-in-windows-forms.md)  
 Gönderen grafik yazıcıya açıklar.  
  
 [Nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Gönderen metin yazıcı açıklar.  
  
 [Nasıl yapılır: Tam bir Windows Forms yazdırma işleri](how-to-complete-windows-forms-print-jobs.md)  
 Kullanıcılar bir yazdırma işinin tamamlanması için uyarı açıklanmaktadır.  
  
 [Nasıl yapılır: Bir Windows formunu yazdırma](how-to-print-a-windows-form.md)  
 Formun geçerli bir kopyasını yazdırmak gösterilmektedir.  
  
 [Nasıl yapılır: Windows Forms'ta baskı önizlemeyi kullanarak yazdırma](how-to-print-in-windows-forms-using-print-preview.md)  
 Nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.PrintPreviewDialog> belge yazdırma için.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [PrintDocument Bileşeni](../controls/printdocument-component-windows-forms.md)  
 Kullanımını açıklayan <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
 [PrintDialog Bileşeni](../controls/printdialog-component-windows-forms.md)  
 Kullanımını açıklayan <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
 [PrintPreviewDialog Denetimi](../controls/printpreviewdialog-control-windows-forms.md)  
 Kullanımını açıklayan <xref:System.Windows.Forms.PrintPreviewDialog> denetimi.  
  
 [PageSetupDialog bileşeni](../controls/pagesetupdialog-component-windows-forms.md)  
 Kullanımını açıklayan <xref:System.Windows.Forms.PageSetupDialog> bileşeni.  
  
 <xref:System.Drawing.Printing>  
 Sınıfları açıklar <xref:System.Drawing.Printing> ad alanı.
