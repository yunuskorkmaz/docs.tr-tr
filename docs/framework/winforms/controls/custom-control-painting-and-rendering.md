---
title: "Özel Denetim Boyama ve İşleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 355a5842348aa4395d1841d0343080ddef634456
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="custom-control-painting-and-rendering"></a>Özel Denetim Boyama ve İşleme
Denetimlerin özel boyama .NET Framework tarafından kolay pek çok karmaşık görevlerden biridir. Bir özel denetim yazarken denetiminizin grafik görünümü ile ilgili birçok seçeneğiniz vardır. Öğesinden devralan bir denetim yazıyorsanız `Control`, grafik gösterimi işlemek, denetim kodu sağlamalısınız. İçinden devralma tarafından bir kullanıcı denetimi oluşturuyorsanız `UserControl`, veya devralan Windows Forms denetimleri her birinden, standart grafik gösterimi geçersiz kılabilir ya da kendi grafik kodunuzu girin. Özel işleme bağlı denetimler için sağlamak istiyorsanız bir `UserControl` geliştirmekte olduğunuz, seçeneklerinizi daha kısıtlı hale, ancak hala çok çeşitli grafik olasılıklarını denetimleri ve uygulamaları sağlar.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms Denetimini İşleme](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 Bir denetim görüntüler mantığı program gösterilmektedir.  
  
 [Kullanıcı Çizimli Denetimler](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 Yazma ve işleme kodu denetlemek için geçersiz kılma adımlarını genel bir bakış sağlar.  
  
 [Bağlı Denetimler](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 Kullanıcı denetimleri ve formlarında bağlı denetimler için özel işleme kodu uygulamak açıklar.  
  
 [Nasıl yapılır: Çalışma Zamanında Denetiminizi Görünmez Yapma](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Visible%2A> denetim gösterme ve gizleme için özellik.  
  
 [Nasıl yapılır: Denetiminize Saydam Arka Plan Verme](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.SetStyle%2A> opak, saydam veya kısmen saydam arka plan rengi oluşturmak için yöntemi.  
  
 [Denetimleri Görsel Stilde İşleme](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 Görsel stiller işletim sistemlerinde desteklemek kullanarak denetimlerini işlemeye gösterilmektedir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Control>  
 Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.  
  
 <xref:System.Windows.Forms.UserControl>  
 Bu sınıf tanımlar ve tüm üyeleri bağlantılar içerir.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Bu yöntem açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 Tanıtır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] daha fazla bilgi için Visual Studio Perspektif ve verir bağlantılardan grafik işlevselliği.  
  
 [Özel Denetim Çeşitleri](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 Özel denetimler, yazabilirsiniz türlerini açıklar.
