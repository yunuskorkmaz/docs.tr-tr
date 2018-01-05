---
title: "Nasıl yapılır: Yol Gradyanı Oluşturma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- path gradients [Windows Forms], creating
- gradients [Windows Forms], creating path
- graphics paths [Windows Forms], creating gradient
ms.assetid: 1948e834-e104-481c-b71d-d8aa9e4d106e
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47a70e55d0f5b6197dc7c77b9e95f2279b814737
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-path-gradient"></a>Nasıl yapılır: Yol Gradyanı Oluşturma
<xref:System.Drawing.Drawing2D.PathGradientBrush> Sınıfı renkleri kademeli olarak değişen bir şekli doldurmak özelleştirmenize olanak tanır. Örneğin, merkezi bir yolu için tek bir renk ve başka bir renk sınırın bir yolu belirtebilirsiniz. Ayrıca her bir yolu sınırları boyunca çeşitli noktalar için ayrı renkleri belirtebilirsiniz.  
  
> [!NOTE]
>  İçinde [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], çizgiler ve eğrilerle tarafından korunan bir dizi yoludur bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi. Hakkında daha fazla bilgi için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] yolları bkz [GDI +'da grafik yolları](../../../../docs/framework/winforms/advanced/graphics-paths-in-gdi.md) ve [Constructing ve çizim yolları](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md).  
  
### <a name="to-fill-an-ellipse-with-a-path-gradient"></a>Elips yol gradyanı ile doldurmak için  
  
-   Aşağıdaki örnek elips yolu gradyan fırçası ile doldurur. Merkezi rengi mavi olarak ayarlanır ve sınır renk açık mavi için ayarlanır. Aşağıdaki çizimde doldurulmuş elips gösterir.  
  
     ![Gradyan yolu](../../../../docs/framework/winforms/advanced/media/pathgradient1.png "pathgradient1")  
  
     Varsayılan olarak, yol sınırının dışında bir yolu gradyan fırçası kapsamaz. Yolun sınırının ötesine genişleten bir şekil doldurmak için yol gradyan fırçası kullanırsanız, alan yolu dışında ekranın doldurulmuş değil.  
  
     Değiştirirseniz olanlar aşağıda gösterildiği <xref:System.Drawing.Graphics.FillEllipse%2A> aşağıdaki kodu çağırın `e.Graphics.FillRectangle(pthGrBrush, 0, 10, 200, 40)`.  
  
     ![Gradyan yolu](../../../../docs/framework/winforms/advanced/media/pathgradient2.png "pathgradient2")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#11)]
     [!code-vb[System.Drawing.UsingaGradientBrush#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#11)]  
  
     Önceki kod örneğinde Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> parametresi e, <xref:System.Windows.Forms.PaintEventHandler>.  
  
### <a name="to-specify-points-on-the-boundary"></a>Sınırında noktaları belirtmek için  
  
-   Aşağıdaki örnek bir yolu gradyan fırçası yıldız şeklinde bir yoldan oluşturur. Kod kümeleri <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterColor%2A> rengi kırmızı yıldızın kütle merkezini adresindeki ayarlar özelliği. Ardından kod kümeleri <xref:System.Drawing.Drawing2D.PathGradientBrush.SurroundColors%2A> çeşitli renkleri belirtmek için özellik (depolanan `colors` array) tek tek noktalarında `points` dizi. Son kod açıklaması yıldız şeklinde yolun yol gradyan fırçası ile doldurur.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#12)]
     [!code-vb[System.Drawing.UsingaGradientBrush#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#12)]  
  
-   Aşağıdaki örnek olmadan yol gradyanı çizer bir <xref:System.Drawing.Drawing2D.GraphicsPath> kodu nesnesi. Belirli <xref:System.Drawing.Drawing2D.PathGradientBrush.%23ctor%2A> örnek oluşturucuda noktalar dizisi alır ancak gerektirmez bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi. Ayrıca, unutmayın <xref:System.Drawing.Drawing2D.PathGradientBrush> bir dikdörtgen bir yol değil doldurmak için kullanılır. Dikdörtgen bazı dikdörtgen olmayan boyanır şekilde fırça tarafından fırça tanımlamak için kullanılan kapalı yol daha büyük. Aşağıdaki çizimde dikdörtgenin (noktalı çizgi) ve yolun gradyan fırçası tarafından boyandığında dikdörtgen bölümünü gösterir.  
  
     ![Gradyan](../../../../docs/framework/winforms/advanced/media/gradient4.png "gradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#13)]
     [!code-vb[System.Drawing.UsingaGradientBrush#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#13)]  
  
### <a name="to-customize-a-path-gradient"></a>Yol gradyanı özelleştirmek için  
  
-   Yolun gradyan fırçası özelleştirmek için bir yoldur ayarlamak için kendi <xref:System.Drawing.Drawing2D.PathGradientBrush.FocusScales%2A> özelliği. Odağı ölçekler ana yolun içinde kaynaklandığını bir iç yolu belirtin. Merkezi renk iç yol içinde yerine yalnızca orta noktası her yerde görüntülenir.  
  
     Aşağıdaki örnek, bir elips yola göre yolu gradyan fırçası oluşturur. Kod mavi kenarlığı rengini ayarlar, açık mavi için merkezi rengini belirler ve ardından elips yolu doldurmak için yolu gradyan fırçası kullanır.  
  
     Ardından, kod yolu gradyan fırçası odak ölçeklerdeki ayarlar. X odak ölçek 0.3 için ayarlanır ve y odak ölçek 0,8 için ayarlanır. Kod çağrıları <xref:System.Drawing.Graphics.TranslateTransform%2A> yöntemi bir <xref:System.Drawing.Graphics> nesne böylece sonraki çağrı <xref:System.Drawing.Graphics.FillPath%2A> ilk elipsin sağında bulunur elips doldurur.  
  
     Odağı ölçekler etkisini görmek için kendi merkezi ile ana elips paylaşır küçük bir elips düşünün. Küçük (iç) elips 0.3 faktörüyle ve dikey olarak 0,8 faktörüyle (ortasından) yatay ölçeklendirilmiş ana elips ' dir. İç elips sınır için bir sınır dış elipsin ilerlerken, renk mavi için açık mavi kademeli olarak değiştirir. Renk kalır açık mavi paylaşılan merkezine iç elipsin sınır taşırken.  
  
     Aşağıdaki çizimde, aşağıdaki kodu çıktısını gösterir. Sol taraftaki elips merkezi noktada yalnızca açık mavi ' dir. Üç nokta sağdaki açık mavi iç yolun içindeki her yerde ' dir.  
  
 ![Gradyan](../../../../docs/framework/winforms/advanced/media/focusscales1nogamma.png "focusscales1NoGamma")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#14)]
 [!code-vb[System.Drawing.UsingaGradientBrush#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#14)]  
  
### <a name="to-customize-with-interpolation"></a>İlişkilendirme özelleştirmek için  
  
-   Yolun gradyan fırçası özelleştirmek için başka bir ilişkilendirme renkleri dizisini ve bir dizi ilişkilendirme konumlarını belirtmek için yoludur.  
  
     Aşağıdaki örnek, bir üçgen üzerinde temel yolu gradyan fırçası oluşturur. Kod kümeleri <xref:System.Drawing.Drawing2D.PathGradientBrush.InterpolationColors%2A> ilişkilendirme renkleri (koyu yeşil, açık mavi, mavi) dizisi ve ilişkilendirme konumlar (0, 0.25, 1) bir dizi belirtmek için yol gradyan fırçası özelliği. Bir sınır üçgen merkezi noktasına ilerlerken, renk açık mavi ve ardından mavi ve açık mavi kademeli olarak koyu yeşilden değiştirir. Mavi koyu yeşil arasındaki uzaklığı yüzde 25'i de koyu yeşil değişimin açık mavi olur.  
  
     Özel yol gradyan fırçası ile dolu üçgen aşağıda gösterilmektedir.  
  
     ![Gradyan yolu](../../../../docs/framework/winforms/advanced/media/pathgradient4.png "pathgradient4")  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#15)]
     [!code-vb[System.Drawing.UsingaGradientBrush#15](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#15)]  
  
### <a name="to-set-the-center-point"></a>Orta noktası ayarlamak için  
  
-   Varsayılan olarak, merkezi bir yolu gradyan fırçası fırça oluşturmak için kullanılan yolu kütle merkezini noktasıdır. Ayarlayarak orta noktasının konumunu değiştirebilirsiniz <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> özelliği <xref:System.Drawing.Drawing2D.PathGradientBrush> sınıfı.  
  
     Aşağıdaki örnek, elips üzerinde temel yolu gradyan fırçası oluşturur. Elips merkezi altındadır (70, 35), ancak yolun gradyan fırçası orta noktası kümesine (120, 40).  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#16)]
     [!code-vb[System.Drawing.UsingaGradientBrush#16](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#16)]  
  
     Aşağıdaki çizimde doldurulmuş elips ve yolun gradyan fırçası orta noktası gösterir.  
  
     ![Gradyan yolu](../../../../docs/framework/winforms/advanced/media/pathgradient5.png "pathgradient5")  
  
-   Yolun gradyan fırçası orta noktası fırça oluşturmak için kullanılan yolu dışında bir yere ayarlayabilirsiniz. Aşağıdaki örnek ayarlamak için çağrı değiştirir <xref:System.Drawing.Drawing2D.PathGradientBrush.CenterPoint%2A> önceki kod bir özellik.  
  
     [!code-csharp[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#17)]
     [!code-vb[System.Drawing.UsingaGradientBrush#17](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#17)]  
  
     Aşağıdaki çizimde, bu değişikliği çıkış gösterir.  
  
     ![Gradyan yolu](../../../../docs/framework/winforms/advanced/media/pathgradient6.png "pathgradient6")  
  
     (Bunlar çok yakın rağmen) Yukarıdaki çizimde, sağ uçta noktaları elipsin saf mavi değildir. Dolgu rengi (0, 0, 255) saf mavi olduğu noktası (145, 35) ulaştıysanız gibi gradyan renkleri konumlandırılır. Ancak dolgu hiçbir zaman ulaştığında (145, 35) yolunu içinde yalnızca bir yol gradyan fırçası boyar olduğundan.  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde Windows Forms ile kullanılmak üzere tasarlanmıştır ve ihtiyaç <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Şekilleri Doldurmak için Gradyan Fırçası Kullanma](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)
