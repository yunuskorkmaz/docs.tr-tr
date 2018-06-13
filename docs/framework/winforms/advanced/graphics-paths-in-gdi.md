---
title: GDI+'da Grafik Yolları
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523895"
---
# <a name="graphics-paths-in-gdi"></a>GDI+'da Grafik Yolları
Yollar çizgiler, dikdörtgenler ve basit Eğriler birleştirerek oluşturulur. Gelen geri çağırma [vektör grafiklerine genel bakış](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) resim çizim için en kullanışlı olması için aşağıdaki temel yapı taşlarının kanıtlanmış:  
  
-   satırları  
  
-   Dikdörtgenler  
  
-   Üç nokta  
  
-   Yaylar  
  
-   Çokgenler  
  
-   Ana Eğriler  
  
-   Bézier eğrileri  
  
 GDI +'daki <xref:System.Drawing.Drawing2D.GraphicsPath> nesne dizisi bu yapı taşları tek bir birimde toplamanızı sağlar. Çizgiler, dikdörtgenler, çokgenler ve eğriler tüm dizisini sonra yapılan bir çağrı ile çizilebilir <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Aşağıdaki çizimde bir satır, bir yay, Bézier eğrisi ve Kardinal eğri birleştirilerek oluşturulan bir yolunu gösterir.  
  
 ![Yol](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>Bir yol kullanarak  
 <xref:System.Drawing.Drawing2D.GraphicsPath> Sınıfı çizilmesi öğelerinin bir dizisini oluşturmak için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (için ana Eğriler), ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>. Bu yöntemlerin her biri aşırı yüklendi; diğer bir deyişle, her bir yöntemin birkaç farklı parametre listesi destekler. Örneğin, bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi alır dört tamsayılar ve başka bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi iki alan <xref:System.Drawing.Point> nesneleri.  
  
 Tek bir çağrı yolunda birkaç öğe ekleme çoğul yardımcı yöntemi çizgiler, dikdörtgenler ve Bézier eğrileri yolunu eklemek için yöntemi vardır: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>. Ayrıca, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> yöntemlerine sahip yardımcı yöntemler <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, eklemek kapalı eğri veya pasta yolu.  
  
 Bir yol çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesne, bir <xref:System.Drawing.Pen> nesnesini ve bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesnesi. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi genişlik ve yolun işlemek için kullanılan çizginin rengini gibi özniteliklerini depolar. <xref:System.Drawing.Drawing2D.GraphicsPath> Nesnesi çizgiler ve yolunu oluşturur eğriler dizisi saklar. <xref:System.Drawing.Pen> Nesne ve <xref:System.Drawing.Drawing2D.GraphicsPath> nesne bağımsız değişken olarak geçirilen <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi. Aşağıdaki örnekte bir satır, elips ve Bézier eğrisi oluşan bir yol çizilmiştir:  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 Aşağıdaki çizimde yolunu gösterir.  
  
 ![Yol](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 Çizgiler, dikdörtgenler ve Eğriler için bir yol ekleme ek olarak, bir yol yolları ekleyebilirsiniz. Bu, büyük ve karmaşık yollar oluşturmak için var olan yollar birleştirmenize olanak sağlar.  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Bir yol ekleyebilirsiniz iki başka öğeler vardır: dizeler ve Pastalar. Bir pasta elips iç bölümüdür. Aşağıdaki örnek, Yayı Kardinal eğri, bir dize ve bir pasta bir yol oluşturur:  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 Aşağıdaki çizimde yolunu gösterir. Unutmayın; bir yolu, bağlı olması gerekmez. Yayı Kardinal eğri, dize ve pasta ayrılır.  
  
 ![Yollar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Yollar Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
