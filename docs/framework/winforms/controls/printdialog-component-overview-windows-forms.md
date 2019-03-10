---
title: PrintDialog Bileşenine Genel Bakış (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: dfd6979c596f47fbc9bf68e3866f7fbc9d1dc21c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723367"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms [PrintDialog](printdialog-component-windows-forms.md) bir yazıcı seçin, yazdırılacak sayfa seçin ve diğer Windows tabanlı uygulamalar ile ilgili ayarları belirlemek için kullanılan bir önceden yapılandırılmış bir iletişim kutusu bir bileşendir. Yazıcı ve yazdırma ile ilgili ayarları Seçimi'yerine kendi iletişim kutusunu yapılandırma için basit bir çözüm kullanın. Kullanıcılar kendi belgeleri pek çok bölümünün yazdırmak etkinleştirebilirsiniz: tüm yazdırma, yazdırma seçili sayfa aralığı veya bir seçim yazdırma. Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılarına hemen tanıdık uygulamalar oluşturun. <xref:System.Windows.Forms.PrintDialog> Bileşeni devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.  
  
## <a name="working-with-the-component"></a>Bileşeni ile çalışma  
 Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntemi. Bu bileşen için ya da tek bir yazdırma işi ile ilgili özellikleri vardır (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya ayrı bir yazıcı ayarlarını (<xref:System.Drawing.Printing.PrinterSettings> sınıfı). Bunlardan biri, buna karşılık, birden çok yazıcılar tarafından paylaşılabilir.  
  
 Bir forma eklendiğinde <xref:System.Windows.Forms.PrintDialog> bileşeni Tepsi Windows Form Tasarımcısı'nın altındaki görünür.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Forms.PrintDialog>
- [PrintDialog Bileşeni](printdialog-component-windows-forms.md)
