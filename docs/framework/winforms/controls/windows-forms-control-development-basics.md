---
title: Denetimleri geliştirmeye yönelik temel bilgiler
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: fab0a76e2f9fdb7e2f89e9d6a10dd9c522a6d8e1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739919"
---
# <a name="windows-forms-control-development-basics"></a>Windows Forms Denetimi Geliştirmenin Esasları
Windows Forms denetim, <xref:System.Windows.Forms.Control?displayProperty=nameWithType>doğrudan veya dolaylı olarak türetilen bir sınıftır. Aşağıdaki listede Windows Forms denetimleri geliştirmeye yönelik yaygın senaryolar açıklanmaktadır:  
  
- Birleşik denetim yazmak için mevcut denetimleri birleştirme.  
  
     Bileşik denetimler, denetim olarak yeniden kullanılabilecek bir kullanıcı arabirimini kapsülle. Bileşik denetime örnek olarak, bir metin kutusu ve sıfırlama düğmesinden oluşan bir denetimdir. Görsel tasarımcılar bileşik denetimler oluşturmak için zengin destek sunar. Bileşik bir denetim yazmak için <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>türetilir. Temel sınıf <xref:System.Windows.Forms.UserControl> alt denetimler için klavye yönlendirmesi sağlar ve alt denetimlerin grup olarak çalışmasını sağlar. Daha fazla bilgi için bkz. [bileşik Windows Forms denetimi geliştirme](developing-a-composite-windows-forms-control.md).  
  
- Varolan bir denetimi özelleştirmek veya işlevselliğine eklemek için genişletme.  
  
     Rengi değiştirilemeyen bir düğme ve kaç kez tıklandığını izleyen ek bir özelliği olan düğme, genişletilmiş denetimlerin örnekleridir. Bundan türeterek ve özellikleri, yöntemleri ve olayları geçersiz kılarak veya ekleyerek herhangi bir Windows Forms denetimini özelleştirebilirsiniz.  
  
- Varolan denetimleri birleştirmez veya genişletmez bir denetim yazar.  
  
     Bu senaryoda, <xref:System.Windows.Forms.Control>taban sınıftan türetirsiniz. Ayrıca, temel sınıfın özelliklerini, yöntemlerini ve olaylarını geçersiz kılabilirsiniz ve ekleyebilirsiniz. Başlamak için bkz. [nasıl yapılır: basit bir Windows Forms denetimi geliştirme](how-to-develop-a-simple-windows-forms-control.md).  
  
 Windows Forms denetimleri için temel sınıf, <xref:System.Windows.Forms.Control>, istemci tarafı Windows tabanlı uygulamalarda görsel görüntü için gereken bir sıhhi tesisat sağlar. <xref:System.Windows.Forms.Control>, bir pencere tutamacı sağlar, ileti yönlendirmeyi işler ve diğer birçok kullanıcı arabirimi olayına ek olarak fare ve klavye olayları sağlar. Gelişmiş Düzen sağlar ve <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>ve diğer birçok farklı görsel görüntülemeye özgü özelliklere sahiptir. Ayrıca, güvenlik, iş parçacığı desteği ve ActiveX denetimleriyle birlikte çalışabilirlik sağlar. Çoğu altyapının temel sınıf tarafından sağlanması nedeniyle, kendi Windows Forms denetimlerinizi geliştirmek oldukça kolaydır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Nasıl yapılır: Basit Bir Windows Forms Denetimi Geliştirme](how-to-develop-a-simple-windows-forms-control.md)
- [Bileşik Windows Forms Denetimi Geliştirme](developing-a-composite-windows-forms-control.md)
- [Nasıl yapılır: İlerleme Durumunu Gösteren Windows Forms Denetimi Oluşturma](how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)
