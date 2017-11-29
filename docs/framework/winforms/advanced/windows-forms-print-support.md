---
title: "Windows Forms Yazdırma Desteği"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- forms [Windows Forms], printing (using designer)
- printing [Windows Forms], Windows Forms, support
- printing [Windows Forms], print support
ms.assetid: a4a2960c-eb70-48e2-b641-cfb222704e46
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 029d5ed424061807cf04446cbb10424ae20afba2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-print-support"></a>Windows Forms Yazdırma Desteği
Windows Forms'ta baskı oluşur öncelikle kullanarak [PrintDocument bileşeni](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md) yazdırmak, kullanıcının etkinleştirmek için bileşen ve [PrintPreviewDialog denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md) denetimi [PrintDialog Bileşen](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) ve [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md) bileşenleri Windows işletim sistemine alışmanızı kullanıcılar için tanıdık bir grafik arabirim sağlar.  
  
 Genellikle, yeni bir örneğini oluşturmak <xref:System.Drawing.Printing.PrintDocument> bileşeni ne kullanarak yazdırma açıklayın özelliklerini ayarlama <xref:System.Drawing.Printing.PrinterSettings> ve <xref:System.Drawing.Printing.PageSettings> sınıfları ve çağrı <xref:System.Drawing.Printing.PrintDocument.Print%2A> gerçekten belgeyi yazdırmayı yöntemi.  
  
 Windows tabanlı bir uygulama yazıcıdan süresince <xref:System.Drawing.Printing.PrintDocument> bileşeni iptal edilmesi uyarı kullanıcıların yazdırma oluştuğunu olgu ve yazdırma işinin izin vermek için bir iptal Yazdır iletişim kutusu gösterilir.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Nasıl yapılır: standart Windows Forms yazdırma işleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-standard-windows-forms-print-jobs.md)  
 Nasıl kullanılacağı açıklanmaktadır <xref:System.Drawing.Printing.PrintDocument> bir Windows formundan yazdırmak için bileşen.  
  
 [Nasıl yapılır: çalışma zamanında bir printdialog'dan kullanıcı girişi yakalama](../../../../docs/framework/winforms/advanced/how-to-capture-user-input-from-a-printdialog-at-run-time.md)  
 Program aracılığıyla kullanarak seçilen yazdırma seçeneklerinin nasıl değiştirileceği açıklanmaktadır <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
 [Nasıl yapılır: Windows Forms'ta bir kullanıcının bilgisayarına bağlanan yazıcıları seçme](../../../../docs/framework/winforms/advanced/how-to-choose-the-printers-attached-to-user-computer-in-windows-forms.md)  
 Kullanarak yazdırmak için yazıcı değiştirme açıklar <xref:System.Windows.Forms.PrintDialog> çalışma zamanında bileşen.  
  
 [Nasıl yapılır: Windows Forms'ta grafik yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)  
 Yazıcı gönderen grafik açıklar.  
  
 [Nasıl yapılır: Windows Forms'ta çok sayfalı metin dosyası yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-a-multi-page-text-file-in-windows-forms.md)  
 Gönderen metin yazıcı açıklar.  
  
 [Nasıl yapılır: tam Windows Forms yazdırma işleri](../../../../docs/framework/winforms/advanced/how-to-complete-windows-forms-print-jobs.md)  
 Yazdırma işi tamamlandığında kullanıcılara uyarı açıklanmaktadır.  
  
 [Nasıl yapılır: bir Windows formunu yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-a-windows-form.md)  
 Geçerli formun bir kopyasını yazdırmak gösterilmiştir.  
  
 [Nasıl yapılır: Windows Forms'ta baskı önizlemeyi kullanarak yazdırma](../../../../docs/framework/winforms/advanced/how-to-print-in-windows-forms-using-print-preview.md)  
 Nasıl kullanılacağını gösteren bir <xref:System.Windows.Forms.PrintPreviewDialog> belge yazdırma için.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [PrintDocument bileşeni](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)  
 Kullanımını açıklar <xref:System.Drawing.Printing.PrintDocument> bileşeni.  
  
 [PrintDialog bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)  
 Kullanımını açıklar <xref:System.Windows.Forms.PrintDialog> bileşeni.  
  
 [PrintPreviewDialog denetimi](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 Kullanımını açıklar <xref:System.Windows.Forms.PrintPreviewDialog> denetim.  
  
 [PageSetupDialog bileşeni](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)  
 Kullanımını açıklar <xref:System.Windows.Forms.PageSetupDialog> bileşeni.  
  
 <xref:System.Drawing.Printing>  
 Sınıflarda açıklar <xref:System.Drawing.Printing> ad alanı.
