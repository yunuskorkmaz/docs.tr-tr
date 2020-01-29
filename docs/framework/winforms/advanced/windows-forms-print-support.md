---
title: Yazdırma desteği
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
ms.openlocfilehash: d6e8f60db7afe2f1b04eaae6fe71aa93e5c22cae
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732498"
---
# <a name="windows-forms-print-support"></a>Windows Forms Yazdırma Desteği
Windows Forms Yazdırma, öncelikle kullanıcının yazdırmasını sağlamak için [PrintDocument bileşen](../controls/printdocument-component-windows-forms.md) bileşenini ve [Printönizleme iletişim kutusu denetim](../controls/printpreviewdialog-control-windows-forms.md) denetimi, [PrintDialog bileşeni](../controls/printdialog-component-windows-forms.md) ve [PageSetupDialog bileşen](../controls/pagesetupdialog-component-windows-forms.md) bileşenlerini kullanarak Windows işletim sistemine alışkın kullanıcılara tanıdık bir grafik arabirimi sağlar.  
  
 Genellikle <xref:System.Drawing.Printing.PrintDocument> bileşenin yeni bir örneğini oluşturur, <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları kullanarak neyin yazdırılacağını tanımlayan özellikleri ayarlar ve belgeyi gerçekten yazdırmak için <xref:System.Drawing.Printing.PrintDocument.Print%2A> yöntemini çağırabilirsiniz.  
  
 Windows tabanlı bir uygulamadan yazdırma işlemi sırasında, <xref:System.Drawing.Printing.PrintDocument> bileşeni, kullanıcıların yazdırmanın meydana geldiğini ve yazdırma işinin iptal edilmesine izin vermek için bir yazdırmayı iptal et iletişim kutusunu gösterecektir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: Standart Windows Forms Yazdırma İşleri Oluşturma](how-to-create-standard-windows-forms-print-jobs.md)  
 <xref:System.Drawing.Printing.PrintDocument> bileşeninin bir Windows formdan yazdırılması için nasıl kullanılacağını açıklar.  
  
 [Nasıl yapılır: Bir PrintDialog'dan Çalışma Zamanında Kullanıcı Girdisi Yakalama](how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Seçilen yazdırma seçeneklerinin <xref:System.Windows.Forms.PrintDialog> bileşeni kullanılarak programlı bir şekilde nasıl değiştirileceği açıklanmaktadır.  
  
 [Nasıl yapılır: Windows Forms'ta Bir Kullanıcının Bilgisayarına Bağlanan Yazıcıları Seçme](how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Çalışma zamanında <xref:System.Windows.Forms.PrintDialog> bileşeni kullanılarak yazdırılacak yazıcının değiştirilmesini açıklar.  
  
 [Nasıl yapılır: Windows Forms'ta Grafik Yazdırma](how-to-print-graphics-in-windows-forms.md)  
 Yazıcıya grafik gönderilmesini açıklar.  
  
 [Nasıl yapılır: Windows Forms'ta Çok Sayfalı Metin Dosyası Yazdırma](how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Yazıcıya metin gönderilmesini açıklar.  
  
 [Nasıl yapılır: Windows Forms Yazdırma İşlerini Tamamlama](how-to-complete-windows-forms-print-jobs.md)  
 Kullanıcılara bir yazdırma işinin tamamlanmasına yönelik nasıl uyarı verileceğini açıklar.  
  
 [Nasıl yapılır: Bir Windows Formunu Yazdırma](how-to-print-a-windows-form.md)  
 Geçerli formun bir kopyasının nasıl yazdırılacağını gösterir.  
  
 [Nasıl yapılır: Windows Forms'ta Baskı Önizlemeyi Kullanarak Yazdırma](how-to-print-in-windows-forms-using-print-preview.md)  
 Belge yazdırmak için <xref:System.Windows.Forms.PrintPreviewDialog> nasıl kullanacağınızı gösterir.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [PrintDocument Bileşeni](../controls/printdocument-component-windows-forms.md)  
 <xref:System.Drawing.Printing.PrintDocument> bileşeninin kullanımını açıklar.  
  
 [PrintDialog Bileşeni](../controls/printdialog-component-windows-forms.md)  
 <xref:System.Windows.Forms.PrintDialog> bileşeninin kullanımını açıklar.  
  
 [PrintPreviewDialog Denetimi](../controls/printpreviewdialog-control-windows-forms.md)  
 <xref:System.Windows.Forms.PrintPreviewDialog> denetiminin kullanımını açıklar.  
  
 [PageSetupDialog bileşeni](../controls/pagesetupdialog-component-windows-forms.md)  
 <xref:System.Windows.Forms.PageSetupDialog> bileşeninin kullanımını açıklar.  
  
 <xref:System.Drawing.Printing>  
 <xref:System.Drawing.Printing> ad alanındaki sınıfları açıklar.
