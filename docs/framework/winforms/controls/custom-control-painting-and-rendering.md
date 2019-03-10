---
title: Özel Denetim Boyama ve İşleme
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: ec9002ffa4a7e2c82f59d52344764a01afe4c568
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722145"
---
# <a name="custom-control-painting-and-rendering"></a>Özel Denetim Boyama ve İşleme
Özel boyama denetimlerin .NET Framework tarafından daha kolay pek çok karmaşık görev biridir. Özel denetim yazarken, denetiminizin grafik görünümü ile ilgili birçok seçeneğiniz vardır. Devralınan bir denetim yazıyorsanız `Control`, Denetim, grafik gösterimi işleme veren kod sağlamanız gerekir. Devralarak bir kullanıcı denetimi oluşturuyorsanız `UserControl`, veya devraldığını Windows Forms denetimleri birinden, standart grafik gösterimi geçersiz kılabilir ya da kendi grafik kodunu sağlayın. Bağlı denetimler için özel işleme sağlamak istiyorsanız bir `UserControl` geliştirmekte olduğunuz, seçeneklerinizi daha sınırlı olur, ancak yine de çok çeşitli grafik denetimleri ve uygulamaları olasılıklarını izin.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Windows Forms Denetimini İşleme](rendering-a-windows-forms-control.md)  
 Bir denetim görüntüler mantığını nasıl programlama yapılacağı gösterilmektedir.  
  
 [Kullanıcı Çizimli Denetimler](user-drawn-controls.md)  
 Yazma ve işleme kodunu denetlemek için geçersiz kılma içinde yer alan adımların bir genel bakış sağlar.  
  
 [Bağlı Denetimler](constituent-controls.md)  
 Bağlı denetimler için özel işleme kodu, kullanıcı denetimleri ve forms uygulanacağını açıklar.  
  
 [Nasıl yapılır: Çalışma zamanında denetiminizi görünmez yapma](how-to-make-your-control-invisible-at-run-time.md)  
 Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.Visible%2A> özelliğini gizler ve bir denetimi gösterir.  
  
 [Nasıl yapılır: Denetiminize saydam arka plan verme](how-to-give-your-control-a-transparent-background.md)  
 Nasıl kullanılacağını gösterir <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemini opak, saydam veya kısmen saydam bir arka plan rengi.  
  
 [Denetimleri Görsel Stilde İşleme](rendering-controls-with-visual-styles.md)  
 Görsel stiller, bunları destekleyen işletim sistemlerinde kullanarak denetimleri nasıl oluşturulacağını gösterir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Control>  
 Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.  
  
 <xref:System.Windows.Forms.UserControl>  
 Bu sınıf açıklar ve tüm üyeleri için bağlantılar içerir.  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 Bu yöntem açıklar.  
  
## <a name="related-sections"></a>İlgili Bölümler  
 [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](../advanced/how-to-create-graphics-objects-for-drawing.md)  
 Tanıtır [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] grafik işlevlerini Perspektif ve size bir Visual Studio bağlantılardan daha fazla bilgi için.  
  
 [Özel Denetim Çeşitleri](varieties-of-custom-controls.md)  
 Özel denetimler, yazabilirsiniz türlerini açıklar.
