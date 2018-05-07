---
title: İki Kez Arabelleğe Alınan Grafikler
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: ea4b4b8616ed0b3eab2ddd6b2ec57a39909a0fce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="double-buffered-graphics"></a>İki Kez Arabelleğe Alınan Grafikler
Grafik programlama olduğunda, titreşimi yaygın sorun kullanır. Birden çok karmaşık Boyama işlemleri gerektiren grafik işlemleri Titreşim veya aksi halde kabul edilebilir bir görünüme sahip görünecek şekilde işlenmiş görüntüleri neden olabilir. Bu sorunları gidermek için .NET Framework iki kez arabelleğe alma erişim sağlar.  
  
 İki kez arabelleğe alma bellek arabelleği birden çok boyama işlemlerle ilişkili titreşimi sorunları ele almak için kullanır. İki kez arabelleğe alma etkinleştirildiğinde, tüm boyama işlemleri ilk ekranda çizim yüzeyini yerine bir arabelleğe işlenir. Tüm boyama işlemleri tamamlandıktan sonra Ara belleğe doğrudan ilişkili çizim yüzeyini kopyalanır. Yalnızca bir grafik işlem ekranda gerçekleştirildiğinden, karmaşık boyama işlemlerle ilişkili görüntü titremeyi ortadan kalkar.  
  
## <a name="default-double-buffering"></a>Varsayılan iki kez arabelleğe alma  
 Uygulamalarınızda iki kez arabelleğe alma kullanmak için en kolay yolu varsayılan formlar ve .NET Framework tarafından sağlanan denetimler için arabelleğe alma çift kullanmaktır. Varsayılan Windows Forms için arabelleğe alma çift etkinleştirebilir ve Windows denetimleri ayarlayarak yazılan <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğine `true` veya kullanarak <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi. Daha fazla bilgi için bkz: [nasıl yapılır: iki kez arabelleğe alma formlar ve denetimler için ile grafik titreşimini azaltma](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Arabelleğe alınan grafikleri elle yönetme  
 Animasyon veya gelişmiş bellek yönetimi gibi daha gelişmiş çift arabelleğe alma senaryolar için .NET Framework sınıfları kendi çift arabelleğe alma mantığını uygulamak için kullanabilirsiniz. Ayırma ve tek tek grafik arabellekleri yönetme sorumlu sınıfı <xref:System.Drawing.BufferedGraphicsContext> sınıfı. Her uygulama etki alanı kendi varsayılan olan <xref:System.Drawing.BufferedGraphicsContext> bu uygulama için arabelleğe alma çift varsayılan yönetir örneği. Çoğu durumda olacaktır, uygulama başına yalnızca bir uygulama etki alanı bu yüzden genelde bir varsayılan <xref:System.Drawing.BufferedGraphicsContext> uygulama başına. Varsayılan <xref:System.Drawing.BufferedGraphicsContext> örnekleri tarafından yönetilen <xref:System.Drawing.BufferedGraphicsManager> sınıfı. Varsayılan bir başvuru almak <xref:System.Drawing.BufferedGraphicsContext> çağırarak örneği <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Ayrıca, ayrılmış bir oluşturabilirsiniz <xref:System.Drawing.BufferedGraphicsContext> grafik açısından yoğun uygulamalar performansını örneği. Nasıl oluşturulacağı hakkında bilgi için bir <xref:System.Drawing.BufferedGraphicsContext> örnek için bkz: [nasıl yapılır: el ile arabelleğe alınan grafikleri yönetme](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Arabelleğe alınan grafikleri elle görüntüleme  
 Bir örneğini kullanabilir <xref:System.Drawing.BufferedGraphicsContext> çağırarak grafik arabellekleri oluşturmak için sınıf <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, bir örneğini döndürür <xref:System.Drawing.BufferedGraphics> sınıfı. A <xref:System.Drawing.BufferedGraphics> nesnesi bir form veya denetim gibi bir işleme yüzeyi ile ilişkili bir bellek arabelleği yönetir.  
  
 Bu örneği sonra <xref:System.Drawing.BufferedGraphics> sınıfı bir bellek içi grafik arabellek işlemeye yönetir. Bellek arabelleği grafiklere işleyebilen <xref:System.Drawing.BufferedGraphics.Graphics%2A>, hangi düzenlemenizi sağlayan bir <xref:System.Drawing.Graphics> doğrudan bellek arabelleği temsil eden nesne. Bunun için boyama <xref:System.Drawing.Graphics> için yaptığınız gibi nesne bir <xref:System.Drawing.Graphics> çizim yüzeyini temsil eden nesne. Tüm grafik arabelleğe Çekildi sonra kullanabileceğiniz <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> ekranında çizim yüzeyini arabellek içeriğini kopyalamak için.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Drawing.BufferedGraphics> sınıfı için bkz: [el ile arabelleğe alınan grafikleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md). İşleme grafik hakkında daha fazla bilgi için bkz: [grafikler ve Windows Forms'ta çizme](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.BufferedGraphics>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphicsManager>  
 [Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)  
 [Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma](../../../../docs/framework/winforms/advanced/how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 [Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)  
 [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
