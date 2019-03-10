---
title: 'Nasıl yapılır: Yol gradyanı oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
ms.openlocfilehash: 6fbe8a78131cb64e28326133a7cc0fbdcbffd46b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720403"
---
# <a name="how-to-create-a-path-gradient"></a>Nasıl yapılır: Yol gradyanı oluşturma
<xref:System.Drawing.Drawing2D.PathGradientBrush> Sınıfı renkleri yavaş yavaş değişen bir şeklin dolgu özelleştirmenize olanak tanır. Örneğin, merkezi bir yolu için bir renk ve başka bir renk için bir yol sınırını belirtebilirsiniz. Ayrıca her bir yol sınırları boyunca birkaç noktası için farklı renkler belirtebilirsiniz.  
  
> [!NOTE]
>  İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], çizgiler ve eğrilerle tarafından bakımı yapılan bir dizi bir yolu olan bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne. Hakkında daha fazla bilgi için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yollarını görmek [GDI +'da grafik yolları](graphics-paths-in-gdi.md) ve [Constructing ve çizim yolları](constructing-and-drawing-paths.md).  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Bir elips yol gradyanı ile doldurmak için  
  
-   Aşağıdaki örnek, bir elips yol gradyan fırçası ile doldurur. Orta rengini Mavi olarak ayarlanır ve sınır rengini Açık Deniz Mavisi olarak ayarlanır. Dolu Elips aşağıda gösterilmiştir.  
  
     ![Gradyan yolu](./media/pathgradient1.png "pathgradient1")  
  
     Varsayılan olarak, bir yolun gradyan fırçası yol sınırının dışında genişletilmez. Yolun sınırının ötesine genişletir bir şekil doldurmak için yol gradyan fırçası kullanırsanız, alan yolu dışında bir ekranın dolu değil.  
  
     Değiştirirseniz ne aşağıdaki çizimde gösterildiği <xref:System.Drawing.Graphics.FillEllipse%2A> aşağıdaki kodu çağırın `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`.  
  
     ![Gradyan yolu](./media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Yukarıdaki kod örneğinde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> bir parametrede e, <xref:System.Windows.Forms.PaintEventHandler>.  
  
### <a name="to-specify-points-on-the-boundary"></a>Sınırında noktaları belirtmek için  
  
-   Aşağıdaki örnek, bir yıldız şeklinde yolundan yolu gradyan fırçası oluşturur. Kod kümeleri <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> özelliği kütle merkezi kırmızı yıldız'ın en rengini ayarlar. Ardından kod kümeleri <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> çeşitli renkleri belirtmek için özelliği (depolanan `colors` dizisi) bireysel noktalarda `points` dizi. Son kod açıklaması yıldız şeklinde yolun yol gradyan fırçası ile doldurur.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   Aşağıdaki örnek bir yol gradyanı olmadan çizer bir <xref:System.Drawing.Drawing2D.GraphicsPath> kodu nesnesi. Belirli <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> örnek oluşturucusunda bir dizi noktaları alır ancak gerektirmez bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne. Ayrıca, <xref:System.Drawing.Drawing2D.PathGradientBrush> bir dikdörtgen bir yol değil doldurmak için kullanılır. Dikdörtgen, bazı dikdörtgen olmayan boyanır şekilde fırça tarafından fırça tanımlamak için kullanılan kapalı yolu fazladır. Dikdörtgenin (noktalı çizgi) ve yolun gradyan fırçası tarafından boyanan dikdörtgenin bir bölümü aşağıda gösterilmiştir.  
  
     ![Gradyan](./media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Yol gradyanı özelleştirmek için  
  
-   Yolun gradyan fırçası özelleştirmenin bir yolu olan ayarlamak için kendi <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> özelliği. Odak ölçekler ana yolun içinde bulunan iç bir yol belirtin. Orta renk her yerde içinde iç yol yerine yalnızca merkez noktasını görüntülenir.  
  
     Aşağıdaki örnek, bir elips yola göre yolu gradyan fırçası oluşturur. Kod sınır rengini Mavi olarak ayarlar, merkezi rengini Açık Deniz Mavisi olarak ayarlar ve ardından elips yol doldurmak için yol gradyan fırçası kullanır.  
  
     Ardından, kod yolu gradyan fırçası odak ölçeklerinin ayarlar. X odak ölçek 0.3 için ayarlanır ve y odak ölçek 0.8 için ayarlanır. Kod çağrıları <xref:System.Drawing.Graphics.TranslateTransform%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne böylece sonraki çağrı <xref:System.Drawing.Graphics.FillPath%2A> yer alan ilk üç noktanın sağındaki elips doldurur.  
  
     Odak ölçekler etkisini görmek için merkezi bir ana elips paylaşan küçük bir elips düşünün. Küçük (iç) üç nokta işaretine (ortasından) 0.3 faktörüyle ve dikey olarak 0.8 faktörüyle yatay olarak Ölçeklendirildi ana elips ' dir. İç elipsin sınır için sınır dış elipsin taşırken, rengini Açık Deniz Mavisi olarak maviye kademeli olarak değiştirir. Deniz Mavisi renk kalır paylaşılan merkezine iç elipsin sınır geçerken.  
  
     Aşağıdaki kodun çıktısı aşağıdaki çizimde gösterilmektedir. Açık Deniz Mavisi merkez noktasını yalnızca en soldaki elips olur. Sağındaki elips aqua iç yolun içinde her yerde ' dir.  
  
 ![Gradyan](./media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>İlişkilendirme özelleştirmek için  
  
-   Yolun gradyan fırçası özelleştirmek için başka bir ilişkilendirme renkler bir dizi ve bir dizi ilişkilendirme konumlarını belirtmek için yoludur.  
  
     Aşağıdaki örnek, bir üçgeni temel yolu gradyan fırçası oluşturur. Kod kümeleri <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> özellik yolu gradyan fırça renkleri (koyu yeşil, Açık Deniz Mavisi, mavi) bir dizi ve bir dizi ilişkilendirme konumları (0, 0.25, 1) belirtmek için. İçin merkez noktasını bir sınır bu üçgen taşırken, renk için Açık Deniz Mavisi, ardından da mavi aqua kademeli olarak koyu yeşilden değiştirir. Koyu Yeşil değişimi için Açık Deniz Mavisi, koyu yeşil, mavi uzaklığı yüzde 25'olmuyor.  
  
     Özel yol gradyan fırçası ile doldurulmuş üçgen aşağıda gösterilmiştir.  
  
     ![Gradyan yolu](./media/pathgradient4.png "pathgradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Merkez noktasını ayarlamak için  
  
-   Varsayılan olarak, merkezi bir yolu gradyan fırçası fırça oluşturmak için kullanılan yolu kütle merkezi noktasıdır. Merkez noktasının konumunu ayarlayarak değiştirebilirsiniz <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> özelliği <xref:System.Drawing.Drawing2D.PathGradientBrush> sınıfı.  
  
     Aşağıdaki örnek, bir üç nokta işaretine göre yolu gradyan fırçası oluşturur. Elips merkezini altındadır (70'ten, 35), ancak yolun gradyan fırçası merkez noktasını ayarlanır (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Dolu Elips ve yolun gradyan fırçası merkez noktasını aşağıdaki çizimde gösterilmektedir.  
  
     ![Gradyan yolu](./media/pathgradient5.png "pathgradient5")  
  
-   Fırça oluşturmak için kullanılan yolu dışında bir konuma yol gradyan fırçası merkez noktasını ayarlayabilirsiniz. Aşağıdaki örnek ayarlamak için yapılan çağrı değiştirir <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> önceki kodda özelliği.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Bu değişiklik ile çıktı aşağıda gösterilmiştir.  
  
     ![Gradyan yolu](./media/pathgradient6.png "pathgradient6")  
  
     (Çok yakın oldukları rağmen) Yukarıdaki çizimde, en sağdaki noktaları olan elipsin saf mavi değildir. Gradyan renklerini dolgu rengi (0, 0, 255) saf mavi ise olacağı noktası (145, 35) gibi eriştiyseniz konumlandırılır. Ancak hiçbir dolgu ulaştığında (145, 35) olduğundan, yol içinde yalnızca yolun gradyan fırçası boyar.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirdikleri <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Şekilleri Doldurmak için Gradyan Fırçası Kullanma](using-a-gradient-brush-to-fill-shapes.md)
