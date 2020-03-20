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
ms.openlocfilehash: cf4dc558c008fb8adfc327a6a894a428e985df03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182641"
---
# <a name="how-to-create-a-path-gradient"></a>Nasıl yapılır: Yol Gradyanı Oluşturma
Sınıf, <xref:System.Drawing.Drawing2D.PathGradientBrush> bir şekli yavaş yavaş değişen renklerle doldurma şeklinizi özelleştirmenize olanak tanır. Örneğin, bir yolun ortası için bir renk ve bir yolun sınırı için başka bir renk belirtebilirsiniz. Ayrıca, bir yolun sınırı boyunca birkaç noktanın her biri için ayrı renkler belirtebilirsiniz.  
  
> [!NOTE]
> GDI+'da yol, bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne tarafından korunan çizgiler ve eğriler dizisidir. GDI+ yolları hakkında daha fazla bilgi için [GDI+'daki Grafik Yolları](graphics-paths-in-gdi.md) ve [Oluşturma ve Çizim Yolları'na](constructing-and-drawing-paths.md)bakın.  

Bu makaledeki örnekler, denetimin <xref:System.Windows.Forms.Control.Paint> olay işleyicisinden çağrılan yöntemlerdir.  

### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Bir elipsi yol degradesi ile doldurmak için  
  
- Aşağıdaki örnek, bir elipsi yol degrade fırçasıyla doldurur. Orta renk maviye, sınır rengi ise aqua olarak ayarlanır. Aşağıdaki resimde dolgulu elips gösterilmektedir.  
  
     ![Degrade Path bir elips doldurur.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse.png)  
  
     Varsayılan olarak, bir yol degrade fırçası yolun sınırıdışında genişlemez. Yol eğimfırçasini, yolun sınırının ötesine uzanan bir şekli doldurmak için kullanırsanız, ekranın yolun dışındaki alanı doldurulmayaz.  
  
     Aşağıdaki resimde, aşağıdaki koddaki <xref:System.Drawing.Graphics.FillEllipse%2A?displayProperty=nameWithType> çağrıyı değiştirirseniz `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`ne olur:  
  
     ![Gradyan Yol, yolun sınırlarının ötesine uzanıyordu.](./media/how-to-create-a-path-gradient/gradient-path-extended-beyond-boundary.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Önceki kod örneği Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> tasarlanmıştır ve e gerektirir, <xref:System.Windows.Forms.PaintEventHandler>hangi bir parametre .  
  
### <a name="to-specify-points-on-the-boundary"></a>Sınırdaki noktaları belirtmek için  
  
- Aşağıdaki örnek, yıldız şeklindeki bir yoldan bir yol degrade fırçası inşa eder. Kod, yıldızın <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> merkezsindeki rengi kırmızıya ayarlayan özelliği ayarlar. Ardından kod, <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> `points` dizideki tek tek noktalarda `colors` çeşitli renkleri (dizide depolanan) belirtmek için özelliği ayarlar. Son kod deyimi, yıldız şeklindeki yolu yol degrade fırçasıyla doldurur.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
- Aşağıdaki örnek, kodda nesne <xref:System.Drawing.Drawing2D.GraphicsPath> olmayan bir yol degradesi çizer. Örnekteki <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> belirli bir oluşturucu bir dizi nokta alır, ancak bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne gerektirmez. Ayrıca, bir <xref:System.Drawing.Drawing2D.PathGradientBrush> dikdörtgen değil, bir yol doldurmak için kullanılır unutmayın. Dikdörtgen, fırçayı tanımlamak için kullanılan kapalı yoldan daha büyüktür, bu nedenle dikdörtgenin bir kısmı fırçayla boyanmamış. Aşağıdaki resimde dikdörtgen (noktalı çizgi) ve dikdörtgenin yol degrade fırçası ile boyanmış kısmı gösterilmektedir:
  
     ![Yol degrade fırçası ile boyanmış degrade kısmı.](./media/how-to-create-a-path-gradient/gradient-painted-path-gradient-brush.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Yol eğimini özelleştirmek için  
  
- Yol degrade fırçasını özelleştirmenin bir yolu, özelliğini <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> ayarlamaktır. Odak ölçekleri, ana yolun içinde yer alan bir iç yolu belirtir. Orta daki renk, yalnızca merkez noktasında değil, bu iç yolun içinde her yerde görüntülenir.  
  
     Aşağıdaki örnek, eliptik bir yola dayalı bir yol degrade fırçası oluşturur. Kod sınır rengini maviye ayarlar, orta rengi aqua olarak ayarlar ve eliptik yolu doldurmak için yol degrade fırçasını kullanır.  
  
     Ardından, kod yol degrade fırçasının odak ölçeklerini ayarlar. x odak ölçeği 0,3 olarak, y odak ölçeği 0,8 olarak ayarlanır. Kod, bir <xref:System.Drawing.Graphics.TranslateTransform%2A> <xref:System.Drawing.Graphics> nesnenin yöntemini çağırır, <xref:System.Drawing.Graphics.FillPath%2A> böylece sonraki çağrı ilk elipsin sağına oturur bir elipsi doldurur.  
  
     Odak ölçeklerinin etkisini görmek için, merkezini ana elipsle paylaşan küçük bir elips hayal edin. Küçük (iç) elips, yatay olarak 0,3 ve dikey olarak 0,8 faktörüyle ölçeklenmiş ana elipstir. Dış elipsin sınırından iç elipsin sınırına doğru ilerlerken, renk maviden kuyruktan yavaş yavaş değişir. İç elipsin sınırından paylaşılan merkeze doğru ilerlerken, renk suda kalır.  
  
     Aşağıdaki resimde aşağıdaki kodun çıktısı gösterilmektedir. Soldaki elips sadece orta noktada ki aqua. Sağdaki elips iç yolun her yerinde aqua.  
  
 ![Odak ölçeklerinin degrade etkisi](./media/how-to-create-a-path-gradient/focus-scales-aqua-inner-outer-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>Enterpolasyon ile özelleştirmek için  
  
- Yol degrade fırçasını özelleştirmenin başka bir yolu, bir dizi enterpolasyon rengi ve bir dizi enterpolasyon pozisyonu belirtmektir.  
  
     Aşağıdaki örnek, üçgene dayalı bir yol degrade fırçası oluşturur. Kod, bir <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> dizi enterpolasyon rengi (koyu yeşil, aqua, mavi) ve bir dizi enterpolasyon pozisyonu (0, 0,25, 1) belirtmek için yol degrade fırçasının özelliğini ayarlar. Üçgenin sınırından merkez noktaya doğru ilerlerken, renk koyu yeşilden aquaya ve sonra sudan maviye doğru kademeli olarak değişir. Koyu yeşilden aqua'ya geçiş, koyu yeşilden maviye olan mesafenin yüzde 25'inde gerçekleşir.  
  
     Aşağıdaki resimde özel yol degrade fırça ile dolu üçgen gösterir.  
  
     ![Üçgen özel yol degrade fırça ile doldurulur.](./media/how-to-create-a-path-gradient/gradient-brush-filled-triangle.png)  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Merkez noktayı ayarlamak için  
  
- Varsayılan olarak, bir yol degrade fırçasının orta noktası, fırçayı oluşturmak için kullanılan yolun merkezsidir. Sınıfın özelliğini ayarlayarak merkez noktanın <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> konumunu değiştirebilirsiniz. <xref:System.Drawing.Drawing2D.PathGradientBrush>  
  
     Aşağıdaki örnek, bir elipsdayalı bir yol gradyan fırça oluşturur. Elipsin merkezi (70, 35) dır, ancak yol degrade fırçasının orta noktası (120, 40) olarak ayarlanır.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Aşağıdaki resimde dolgulu elips ve yol gradyan fırçanın orta noktası gösterilmektedir:  
  
     ![Dolu elips ve orta nokta ile Gradyan Yol.](./media/how-to-create-a-path-gradient/gradient-path-filled-ellipse-center-point.png)  
  
- Yol degrade fırçasının orta noktasını, fırçayı oluşturmak için kullanılan yolun dışındaki bir konuma ayarlayabilirsiniz. Aşağıdaki örnek, <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> önceki koddaki özelliği ayarlamak için yapılan çağrının yerini alır.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Aşağıdaki resimde bu değişiklikle çıktı gösterilmektedir:  
  
     ![Yolun dışındaki merkez noktası olan Degrade Yolu.](./media/how-to-create-a-path-gradient/gradient-path-center-point-outside.png)  
  
     Önceki resimde, elipsin en sağındaki noktalar saf mavi değildir (çok yakın olmalarına rağmen). Degradedeki renkler, dolgu, rengin saf mavi (0, 0, 0, 255) olacağı noktaya (145, 35) ulaşmış gibi konumlandırılır. Ama dolgu asla (145, 35) ulaşır, çünkü bir yol degrade fırça sadece kendi yolunun içinde boyar.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekler Windows Formlar ile kullanılmak üzere <xref:System.Windows.Forms.PaintEventArgs> `e`tasarlanmıştır ve <xref:System.Windows.Forms.Control.Paint> olay işleyicisinin bir parametresi olan bir parametre gerektirir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Şekilleri Doldurmak için Gradyan Fırçası Kullanma](using-a-gradient-brush-to-fill-shapes.md)
