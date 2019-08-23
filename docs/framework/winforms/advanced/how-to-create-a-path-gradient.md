---
title: 'Nasıl yapılır: Yol Gradyanı Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 8399a56fca87704e10456a4cf8109d7c80d4db45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964411"
---
# <a name="how-to-create-a-path-gradient"></a>Nasıl yapılır: Yol Gradyanı Oluşturma
<xref:System.Drawing.Drawing2D.PathGradientBrush> Sınıfı, bir şekli aşamalı olarak değişen renklerle doldurmanıza olanak sağlar. Örneğin, bir yolun ortası için bir renk ve yolun sınırı için başka bir renk belirtebilirsiniz. Ayrıca, bir yolun sınırı boyunca birkaç noktadan her biri için ayrı renkler belirtebilirsiniz.  
  
> [!NOTE]
> GDI+ ' da, bir yol bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne tarafından tutulan çizgiler ve eğrilerden oluşan bir dizidir. GDI+ yolları hakkında daha fazla bilgi için bkz. [GDI+ Içindeki grafik yolları](graphics-paths-in-gdi.md) ve [yolları oluşturma ve çizme](constructing-and-drawing-paths.md).  

Bu makaledeki örnekler, bir denetimin <xref:System.Windows.Forms.Control.Paint> olay işleyicisinden çağrılan yöntemlerdir.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Bir elipsi yol degradeyle doldurmanız için  
  
- Aşağıdaki örnek, bir elipsi yol gradyan fırçası ile doldurur. Merkez rengi mavi olarak ayarlanır ve sınır rengi deniz mavisi olarak ayarlanır. Aşağıdaki çizimde doldurulmuş elips gösterilmektedir.  
  
     ![Gradyan yolu bir elipsi doldurur.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Varsayılan olarak, bir yol gradyan fırçası yolun sınırının dışına genişlemez. Yolun sınırının ötesine geçen bir şekli doldurmak için yol gradyan fırçası ' nı kullanırsanız, yolun dışındaki ekranın alanı doldurulmaz.  
  
     Aşağıdaki resimde aşağıdaki <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`kodda yapılan çağrıyı değiştirirseniz ne olacağı gösterilmektedir:  
  
     ![Gradyan yolu yolun sınırının ötesine genişletildi.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Yukarıdaki kod örneği, Windows Forms ile kullanım için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.PaintEventHandler>parametresi olan e 'yi gerektirir.  
  
### <a name="to-specify-points-on-the-boundary"></a>Sınır üzerine noktaları belirtmek için  
  
- Aşağıdaki örnek, yıldız şeklindeki bir yoldan yol gradyan fırçası oluşturur. Kod, yıldızın <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> centroıd kısmındaki rengi kırmızı olarak ayarlayan özelliği ayarlar. Daha sonra kod, <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> `points` dizideki tek noktalarda çeşitli renkler ( `colors` dizide depolanır) belirtmek için özelliğini ayarlar. Son kod ifadesinde, yıldız şeklindeki yol gradyan fırçası ile doldurulur.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Aşağıdaki örnek, koddaki bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne olmadan bir yol gradyanı çizer. Örnekteki belirli <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> Oluşturucu bir dizi işaret alır, ancak bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne gerektirmez. Ayrıca, bir yolu değil <xref:System.Drawing.Drawing2D.PathGradientBrush> dikdörtgeni dolduriçin kullanıldığını unutmayın. Dikdörtgen, fırçayı tanımlamak için kullanılan kapalı yoldan daha büyükse, dikdörtgenden bazıları fırça tarafından boyanmaz. Aşağıdaki çizimde, dikdörtgenin (noktalı çizgi) ve yolun gradyan fırçası tarafından boyanmış olan kısmı gösterilmektedir: 
  
     ![Yol gradyan fırçası tarafından boyanan gradyan bölümü.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Yol degradesini özelleştirmek için  
  
- Yol gradyan fırçası 'nı özelleştirmenin bir yolu, <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> özelliğini ayarlamaya yönelik bir yoldur. Odak ölçeği, ana yolun içinde yer alan bir iç yol belirtir. Merkez rengi, yalnızca orta nokta yerine bu iç yolun içinde her yerde görüntülenir.  
  
     Aşağıdaki örnek, elips yolunu temel alan bir yol gradyan fırçası oluşturur. Kod, sınır rengini mavi olarak ayarlar, orta rengi deniz mavisi olarak ayarlar ve ardından elips yolunu dolduracak şekilde yol gradyan fırçası kullanır.  
  
     Daha sonra kod, yol gradyan fırçasının odak ölçeklerini ayarlar. X odak Ölçeği 0,3 olarak ayarlanır ve y odak Ölçeği 0,8 olarak ayarlanır. Kod, sonraki çağrının <xref:System.Drawing.Graphics.TranslateTransform%2A> ilk elipsin sağına <xref:System.Drawing.Graphics> oturan bir elipsi doldurması için <xref:System.Drawing.Graphics.FillPath%2A> bir nesnenin yöntemini çağırır.  
  
     Odak ölçeklerinin etkisini görmek için ana elips ile merkezini paylaşan küçük bir elips düşünün. Küçük (iç) elips, 0,3 faktörü ile yatay olarak ölçeklendirilen ana elips (merkeziyle yaklaşık olarak) ve 0,8 faktörüyle dikey olarak ayarlanır. Dış elips sınırından iç elipsin sınırına geçtiğinizde, renk mavi ile deniz mavisi arasında değişir. İç elipsin sınırından paylaşılan merkezine geçtiğinizde, renk deniz mavisi kalır.  
  
     Aşağıdaki çizimde aşağıdaki kodun çıkışı gösterilmektedir. Sol taraftaki elips yalnızca merkez noktada açık olur. Sağdaki elips, iç yolun içindeki her yerde açık bir şekilde bulunur.  
  
 ![Odak ölçeklerinin gradyan etkisi](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>İlişkilendirme ile özelleştirmek için  
  
- Yol gradyan fırçası 'nı özelleştirmenin başka bir yolu da enterpolasyon renkleri dizisi ve ilişkilendirme konumları dizisi belirtmektir.  
  
     Aşağıdaki örnek, bir üçgeni temel alan bir yol gradyan fırçası oluşturur. Kod, yol gradyanı <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> fırçasının özelliğini, bir enterpolasyon renkleri dizisi (koyu yeşil, deniz mavisi, mavi) ve ilişkilendirme konumları dizisi (0, 0,25, 1) belirtmek için ayarlar. Üçgenin sınırından orta noktaya geçtiğinizde, renk koyu yeşil ve sonra deniz mavisi ile mavi arasında değişir. Koyu yeşil ile deniz mavisi arasındaki değişiklik, koyu yeşil ile mavi arasındaki uzaklığın yüzde 25 ' i oranında olur.  
  
     Aşağıdaki çizimde, özel yol gradyan fırçası ile doldurulmuş üçgen gösterilmektedir.  
  
     ![Özel yol gradyan fırçası ile doldurulmuş üçgen.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Merkez noktasını ayarlamak için  
  
- Varsayılan olarak, bir yol gradyan fırçasının orta noktası, fırçayı oluşturmak için kullanılan yolun centroıd 'si olur. <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> Sınıfın özelliğini<xref:System.Drawing.Drawing2D.PathGradientBrush> ayarlayarak merkez noktasının konumunu değiştirebilirsiniz.  
  
     Aşağıdaki örnek, bir elips temelinde yol gradyan fırçası oluşturur. Elips Merkezi (70, 35), ancak yol gradyan fırçasının orta noktası (120, 40) olarak ayarlanır.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Aşağıdaki çizimde, yol gradyan fırçasının doldurulmuş elips ve orta noktası gösterilmektedir:  
  
     ![Dolgulu elips ve orta nokta ile gradyan yolu.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Bir yol gradyanı fırçasının merkez noktasını, fırçayı oluşturmak için kullanılan yolun dışında bir konuma ayarlayabilirsiniz. Aşağıdaki örnek, önceki kodda <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> özelliğini ayarlamak için çağrısının yerini alır.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Aşağıdaki çizim, bu değişikliğe sahip çıktıyı göstermektedir:  
  
     ![Merkez noktası yol dışında bir gradyan yolu.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Yukarıdaki çizimde, elipsin en sağdaki noktaları saf mavi değildir (çok yakın olsa da). Gradyandaki renkler, rengin saf mavi (0, 0, 255) olacağı noktaya (145, 35) ulaşmış gibi konumlandırılır. Ancak, bir yol gradyan fırçası yalnızca yolunun içinde boyaydığı için Fill hiçbir an (145, 35) öğesine ulaşmaz.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekler, Windows Forms kullanımı için tasarlanmıştır ve <xref:System.Windows.Forms.PaintEventArgs> <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan gerektirir `e`.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Gradyan Fırçası Kullanma](using-a-gradient-brush-to-fill-shapes.md)
