---
title: İki Kez Arabelleğe Alınan Grafikler
ms.date: 03/30/2017
helpviewer_keywords:
- double buffering
- graphics [Windows Forms], double-buffered
- flicker [Windows Forms], reducing with double buffering
- examples [Windows Forms], double-buffered graphics
ms.assetid: 4f6fef99-0972-436e-9d73-0167e4033f71
ms.openlocfilehash: 20ec03e6b84110f7ea00c134dc18b23f233c5f58
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59103447"
---
# <a name="double-buffered-graphics"></a>İki Kez Arabelleğe Alınan Grafikler
Titreşim yaygın grafik programlamada bir sorundur. Birden çok karmaşık boyama işlem gerektiren bir grafik işlem Titreşim veya aksi halde kabul edilemez bir görünüme sahip gibi görünüyor işlenmiş görüntülere neden olabilir. Bu sorunları gidermek için .NET Framework iki kez arabelleğe alma erişim sağlar.  
  
 İki kez arabelleğe almayı bellek arabelleği birden çok Boya işlemleriyle ilişkili titreşimini sorunları ele almak için kullanır. İki kez arabelleğe alma etkinleştirildiğinde, tüm Boya işlemleri ilk ekranda çizim yüzeyi yerine bir arabelleğe işlenir. Tüm Boya işlemleri tamamlandıktan sonra doğrudan ilişkili çizim yüzeyi ara belleğe kopyalanır. Yalnızca bir grafik işlem ekranda gerçekleştirildiğinden, karmaşık boyama işlemleriyle ilişkili görüntü titremeyi ortadan kalkar.  
  
## <a name="default-double-buffering"></a>Varsayılan iki kez arabelleğe alma  
 Uygulamalarınızda iki kez arabelleğe alma kullanmak için en kolay yolu varsayılan formlar ve .NET Framework tarafından sağlanan denetimler için arabelleğe alma çift kullanmaktır. Varsayılan, Windows Forms için arabelleğe alma çift etkinleştirebilir ve Windows denetimleri ayarlayarak yazılan <xref:System.Windows.Forms.Control.DoubleBuffered%2A> özelliğini `true` kullanarak veya <xref:System.Windows.Forms.Control.SetStyle%2A> yöntemi. Daha fazla bilgi için [nasıl yapılır: Formlar ve denetimler için çift arabelleğe alma ile grafik titreşimini azaltma](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md).  
  
## <a name="manually-managing-buffered-graphics"></a>Arabelleğe alınan grafikleri elle yönetme  
 Animasyon veya gelişmiş bellek yönetimi gibi daha gelişmiş çift arabelleğe alma senaryolar için .NET Framework sınıfları kendi iki kez arabelleğe alma mantığını uygulamak için kullanabilirsiniz. Ayırma ve tek bir grafik arabellekleri yönetmekten sorumlu bir sınıfı <xref:System.Drawing.BufferedGraphicsContext> sınıfı. Her uygulama etki alanı kendi varsayılan sahip <xref:System.Drawing.BufferedGraphicsContext> tüm bu uygulama için arabelleğe alma çift varsayılan yönetir örneği. Çoğu durumda olacaktır, uygulama başına yalnızca bir uygulama etki alanı genellikle bir varsayılan olduğundan <xref:System.Drawing.BufferedGraphicsContext> uygulama başına. Varsayılan <xref:System.Drawing.BufferedGraphicsContext> tarafından yönetilen örnekler <xref:System.Drawing.BufferedGraphicsManager> sınıfı. Varsayılan başvuru alabilirsiniz <xref:System.Drawing.BufferedGraphicsContext> çağırarak örneği <xref:System.Drawing.BufferedGraphicsManager.Current%2A>. Ayrıca, ayrılmış bir oluşturabilirsiniz <xref:System.Drawing.BufferedGraphicsContext> örnek grafik açısından yoğun uygulamaların performansını iyileştirebilir. Nasıl oluşturulacağı hakkında daha fazla bilgi için bir <xref:System.Drawing.BufferedGraphicsContext> örneği için bkz. [nasıl yapılır: Arabelleğe alınan grafikleri elle yönetme](how-to-manually-manage-buffered-graphics.md).  
  
## <a name="manually-displaying-buffered-graphics"></a>Arabelleğe alınan grafikleri elle görüntüleme  
 Bir örneğini kullanabilir <xref:System.Drawing.BufferedGraphicsContext> çağırarak grafik arabellekleri oluşturmak için sınıf <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A?displayProperty=nameWithType>, örneğini döndüren <xref:System.Drawing.BufferedGraphics> sınıfı. A <xref:System.Drawing.BufferedGraphics> nesne bir form veya denetim gibi bir işleme yüzeyi ile ilişkili bir bellek arabelleğini yöneten.  
  
 Örneği oluşturulduğu sonra <xref:System.Drawing.BufferedGraphics> sınıfı bir bellek içi grafik arabelleği işlemeye yönetir. Bellek arabelleği grafiklere işleyebilen <xref:System.Drawing.BufferedGraphics.Graphics%2A>, kullanıma sunan bir <xref:System.Drawing.Graphics> doğrudan bellek arabelleği temsil eden nesne. Bunun için boyama <xref:System.Drawing.Graphics> için yaptığınız gibi nesne bir <xref:System.Drawing.Graphics> çizim yüzeyi temsil eden nesne. Tüm grafik arabelleğe Çekildi sonra kullanabileceğiniz <xref:System.Drawing.BufferedGraphics.Render%2A?displayProperty=nameWithType> ekranda çizim yüzeyi arabellek içeriği kopyalamak için.  
  
 Kullanma hakkında daha fazla bilgi için <xref:System.Drawing.BufferedGraphics> sınıfı [el ile arabelleğe alınan grafikleri oluşturma](how-to-manually-render-buffered-graphics.md). Grafik işleme hakkında daha fazla bilgi için bkz. [grafikler ve çizim Windows Forms](graphics-and-drawing-in-windows-forms.md)  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.BufferedGraphics>
- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphicsManager>
- [Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle İşleme](how-to-manually-render-buffered-graphics.md)
- [Nasıl yapılır: Formlar ve Denetimler için İki Kez Arabelleğe Alma ile Grafik Titreşimini Azaltma](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)
- [Nasıl yapılır: Arabelleğe Alınan Grafikleri Elle Yönetme](how-to-manually-manage-buffered-graphics.md)
- [Windows Formlarında Grafikler ve Çizim](graphics-and-drawing-in-windows-forms.md)
