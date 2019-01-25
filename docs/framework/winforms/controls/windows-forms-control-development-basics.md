---
title: Windows Forms Denetimi Geliştirmenin Esasları
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: b40c45905c65cdc40d77553a93e83aa417199826
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643565"
---
# <a name="windows-forms-control-development-basics"></a>Windows Forms Denetimi Geliştirmenin Esasları
Bir Windows Forms denetimi doğrudan veya dolaylı olarak türetildiği bir sınıf olan <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Aşağıdaki listede, Windows Forms denetimleri geliştirme ile ilgili yaygın senaryolar açıklanmaktadır:  
  
-   Bileşik denetim yazma birleştirme varolan denetler.  
  
     Bileşik denetimler bir denetim olarak yeniden kullanılabilir bir kullanıcı arabirimini kapsüller. Bileşik denetim örneği, bir metin kutusu ve Sıfırla düğmesi oluşan bir denetimdir. Görsel tasarımcılar bileşik denetimler oluşturmak için zengin destek sunar. Bileşik denetim yazma için türetilen <xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>. Temel sınıf <xref:System.Windows.Forms.UserControl> alt denetler ve bir grup olarak çalışması alt denetimler sağlar klavye yönlendirme sağlar. Daha fazla bilgi için [bir bileşik Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md).  
  
-   Varolan bir denetimi özelleştirebilir veya işlevselliği eklemek için genişletme.  
  
     Bir düğme rengi değiştirilemez ve kaç kez, tıklanan izleyen ek bir özellik bulunan bir düğme genişletilmiş denetimler örnekleridir. Herhangi bir Windows Forms denetimi türetmeniz ve geçersiz kılma veya özellikleri, yöntemleri ve olayları ekleyerek özelleştirebilirsiniz.  
  
-   Daha önceden bir denetim yazma birleştirebilir veya mevcut denetimleri genişletin.  
  
     Bu senaryoda, denetiminizin temel sınıfından türetilir. <xref:System.Windows.Forms.Control>. Ekleme yapabilir özellikleri, yöntemleri ve temel sınıf olayları geçersiz kılar. Başlamak için bkz: [nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md).  
  
 Windows Forms denetimleri için taban sınıf <xref:System.Windows.Forms.Control>, istemci tarafında Windows tabanlı uygulamalarda visual görüntülemek için gerekli ayarlamaları sağlar. <xref:System.Windows.Forms.Control> bir pencere tutucu sağlayan, ileti yönlendirme işler ve fare ve klavye olaylarını ve bunun yanı sıra diğer birçok kullanıcı arabirimi olayları sağlar. Gelişmiş düzeni sağlar ve görsel görüntüsüne özgü özellikleri vardır <xref:System.Windows.Forms.Control.ForeColor%2A>, <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.Height%2A>, <xref:System.Windows.Forms.Control.Width%2A>ve diğer birçok. Ayrıca, güvenlik, iş parçacığı oluşturma desteği ve ActiveX denetimleri ile birlikte çalışabilirlik sağlar. Çok altyapısının temel sınıfı tarafından sağlandığından, kendi Windows Forms denetimleri geliştirme oldukça kolaydır.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Nasıl yapılır: Basit bir Windows Forms denetimi geliştirme](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)
- [Bileşik Windows Forms Denetimi Geliştirme](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)
- [Nasıl yapılır: İlerleme durumunu gösteren Windows Forms denetimi oluşturma](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)
- [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
