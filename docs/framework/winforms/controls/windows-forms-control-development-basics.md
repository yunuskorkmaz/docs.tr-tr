---
title: "Windows Forms Denetimi Geliştirmenin Esasları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca2bac983e25ab7453230a6718fe7eaa98e82275
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-forms-control-development-basics"></a>Windows Forms Denetimi Geliştirmenin Esasları
Bir Windows Forms denetimi doğrudan veya dolaylı olarak türeyen bir sınıf olan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Aşağıdaki listede Windows Forms denetimleri geliştirme için genel senaryolar açıklanmaktadır:  
  
-   Bileşik denetim yazma birleştirme varolan denetler.  
  
     Bileşik denetimler bir denetim olarak yeniden kullanılabilir kullanıcı arabirimi kapsüller. Bir metin kutusu ve Sıfırla düğmesi oluşan bir denetim bileşik denetim örnektir. Görsel tasarımcılar bileşik denetimleri oluşturmak için zengin destek sunar. Bileşik Denetim yazmak için türetilen <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Taban sınıfı <xref:System.Windows.Forms.UserControl> alt denetimleri ve bir grup olarak çalışmak alt denetimleri sağlar klavye yönlendirme sağlar. Daha fazla bilgi için bkz: [bileşik Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
-   Varolan denetimi özelleştirmek için ya da kendi işlevini eklemek için genişletme.  
  
     Tıklanan kaç kez izleyen ek özelliğine sahip bir düğmeyi ve rengini değiştirilemez bir düğme genişletilmiş denetimler örnekleridir. Herhangi bir Windows Forms denetimi bundan türetilen ve geçersiz kılma özellikleri, yöntemleri ve olayları ekleyerek veya özelleştirebilirsiniz.  
  
-   Mevcut bir denetim yazma birleştirebilir veya mevcut denetimleri genişletir.  
  
     Bu senaryoda, denetim temel sınıfından türetilen <xref:System.Windows.Forms.Control>. Eklemek yanı sıra özellikleri, yöntemleri ve temel sınıf olayları geçersiz kılar. Başlamak için bkz: [nasıl yapılır: basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 Windows Forms denetimleri için temel sınıf <xref:System.Windows.Forms.Control>, istemci-tarafı Windows tabanlı uygulamalarda görsel görüntü için gerekli tesisat sağlar. <xref:System.Windows.Forms.Control>bir pencere tanıtıcının sağlayan, ileti yönlendirme işler ve fare ve klavye olaylarının yanı sıra diğer birçok kullanıcı arabirimi olayları sağlar. Gelişmiş Düzen sağlar ve görsel görüntü için belirli özellikler gibi sahip <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>ve diğer birçok. Ayrıca, güvenlik, iş parçacığı destek ve ActiveX denetimleri ile birlikte çalışabilirlik sağlar. Çok altyapısının temel sınıfı tarafından sağlandığından, kendi Windows Forms denetimleri geliştirme oldukça kolaydır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Nasıl yapılır: basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [Bileşik Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [Nasıl yapılır: ilerleme durumunu gösteren bir Windows Forms denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [Özel denetim çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
