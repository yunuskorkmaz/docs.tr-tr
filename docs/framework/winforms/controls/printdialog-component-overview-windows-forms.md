---
title: "PrintDialog Bileşenine Genel Bakış (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0b90d94165de6985b43d47809ae57bfcae204f0b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog Bileşenine Genel Bakış (Windows Forms)
Windows Forms [PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md) bir yazıcı seçin, yazdırmak için sayfaları seçin ve Windows tabanlı uygulamalar içindeki yazdırma ilgili diğer ayarları belirlemek için kullanılan önceden yapılandırılmış iletişim kutusunu bir bileşendir. Yazıcı ve kendi iletişim kutusu yapılandırma yerine yazdırma ilgili ayarlar seçimi için basit bir çözüm kullanın. Kullanıcılar kendi belgelerini birçok bölümlerini yazdırmak etkinleştirebilirsiniz: tüm yazdırma, seçili sayfa aralığını yazdırmak veya bir seçim yazdırma. Standart Windows iletişim kutularında bağlı olarak, temel işlevleri kullanıcılara hemen alışkın olduğu uygulamalar oluşturun. <xref:System.Windows.Forms.PrintDialog> Bileşen devraldığı <xref:System.Windows.Forms.CommonDialog> sınıfı.  
  
## <a name="working-with-the-component"></a>Bileşeni ile çalışma  
 Kullanım <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> çalışma zamanında iletişim kutusunu görüntülemek için yöntem. Bu bileşen ya da tek bir yazdırma işi ile ilgili özellikleri vardır (<xref:System.Drawing.Printing.PrintDocument> sınıfı) veya ayrı bir yazıcı ayarları (<xref:System.Drawing.Printing.PrinterSettings> sınıfı). Bunlardan, buna karşılık, birden çok yazıcı tarafından paylaşılabilir.  
  
 Bir form için eklendiğinde <xref:System.Windows.Forms.PrintDialog> Tepsisi Windows Forms Tasarımcısı'nın altındaki Bileşen görünür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Forms.PrintDialog>  
 [PrintDialog Bileşeni](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
