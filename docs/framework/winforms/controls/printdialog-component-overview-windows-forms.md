---
title: PrintDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 4df3266cecd080d11d13af8d4678a5303fd669cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54516934"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) bir yazıcı seçin, yazdırılacak sayfa seçin ve diğer Windows tabanlı uygulamalar ile ilgili ayarları belirlemek için kullanılan bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir. Yazıcı ve yazdırma ile ilgili ayarları Seçimi'yerine kendi iletişim kutusunu yapılandırma için basit bir çözüm kullanın. Kullanıcılar kendi belgeleri pek çok bölümünün yazdırmak etkinleştirebilirsiniz: tüm yazdırma, yazdırma seçili sayfa aralığı veya bir seçim yazdırma. Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılarına hemen tanıdık uygulamalar oluşturun. <xref:System.Windows.Forms.PrintDialog> Bileşeni devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.  
  
## <a name="working-with-the-component"></a>Bileşeni ile çalışma  
 Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi. Bu bileşen için ya da tek bir yazdırma işi ile ilgili özellikleri vardır (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya ayrı bir yazıcı ayarlarını (<xref:System.Drawing.Printing.PrinterSettings> sınıfı). Bunlardan biri, buna karşılık, birden çok yazıcılar tarafından paylaşılabilir.  
  
 Bir forma eklendiğinde <xref:System.Windows.Forms.PrintDialog> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog Bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
