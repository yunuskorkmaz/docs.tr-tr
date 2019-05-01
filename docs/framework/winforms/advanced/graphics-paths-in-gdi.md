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
ms.openlocfilehash: c9a43065210f5ef0fffcae01cc7eb88349696b6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938164"
---
# <a name="graphics-paths-in-gdi"></a>GDI+'da Grafik Yolları
Yolları çizgiler, dikdörtgenler ve basit eğrileri birleştirerek oluşturulur. Geri çekilemedi [vektör grafiklerine genel bakış](vector-graphics-overview.md) resimler çizmek için en kullanışlı olması için aşağıdaki temel yapı taşlarını kanıtladıktan:  
  
- satırları  
  
- Dikdörtgenler  
  
- Ellipses  
  
- Yay  
  
- Çokgenler  
  
- Ana Eğriler  
  
- Bézier eğrileri  
  
 GDI +'ta, <xref:System.Drawing.Drawing2D.GraphicsPath> nesne, bu yapı taşlarını bir dizi tek bir birimde toplamanıza olanak sağlar. Tüm satırları, dikdörtgenler, çokgenler ve eğriler dizisini ardından bir çağrı ile kurulabilir <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Aşağıdaki çizimde, bir satır, bir yay Bézier eğri ve Kardinal eğri birleştirilerek oluşturulan bir yolunu gösterir.  
  
 ![Path](./media/aboutgdip02-art14.gif "Aboutgdip02_art14")  
  
## <a name="using-a-path"></a>Bir yol kullanma  
 <xref:System.Drawing.Drawing2D.GraphicsPath> Sınıfı çizilecek öğelerinin bir dizisini oluşturmak için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (için ana Eğriler), ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>. Bu yöntemlerin her biri aşırı yüklendi; diğer bir deyişle, her bir yöntemin birkaç farklı parametre listelerini destekler. Örneğin, bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi alır dört tamsayının ve başka bir çeşitlemesi <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> yöntemi iki alan <xref:System.Drawing.Point> nesneleri.  
  
 Çizgiler ve dikdörtgenler Bézier eğrileri yolu eklemek için yöntemi birkaç öğeleri tek bir arama yoluna ekle çoğul yardımcı yöntemleri vardır: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>. Ayrıca, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> yöntemlerine sahip yardımcı yöntemler <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> ve <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, ekleyen bir kapalı eğri ya da pasta yolu.  
  
 Bir yol çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi bir <xref:System.Drawing.Pen> nesnesi ve bir <xref:System.Drawing.Drawing2D.GraphicsPath> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi ve <xref:System.Drawing.Pen> nesneyi genişlik ve yolun işlemek için kullanılan çizginin rengi gibi özniteliklerini depolar. <xref:System.Drawing.Drawing2D.GraphicsPath> Çizgiler ve eğrilerle yolu kolaylaştıran bir dizi nesnesini depolar. <xref:System.Drawing.Pen> Nesne ve <xref:System.Drawing.Drawing2D.GraphicsPath> nesne bağımsız değişkenleri olarak geçirilir <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi. Aşağıdaki örnek, bir satır, bir elips ve Bézier eğri oluşan bir yol çizer:  
  
 [!code-csharp[LinesCurvesAndShapes#101](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 Aşağıdaki çizimde yolunu gösterir.  
  
 ![Path](./media/aboutgdip02-art15.gif "Aboutgdip02_art15")  
  
 Çizgiler, dikdörtgenler ve eğriler yolunu eklemenin yanı sıra, bir yol yollar ekleyebilirsiniz. Bu, büyük ve karmaşık yolları oluşturmak için mevcut yolları birleştirmenize olanak sağlar.  
  
 [!code-csharp[LinesCurvesAndShapes#102](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 Yolu ekleyebileceğiniz iki öğe: dizeleri ve pasta. Bir pasta, bir elipsin iç bölümüdür. Aşağıdaki örnek, Yayı Kardinal eğri, bir dize ve bir pasta bir yol oluşturur:  
  
 [!code-csharp[LinesCurvesAndShapes#103](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 Aşağıdaki çizimde yolunu gösterir. Unutmayın; bir yolu, bağlı olması gerekmez. Yayı Kardinal eğri, dize ve pasta ayrılır.  
  
 ![Paths](./media/aboutgdip02-art16.gif "Aboutgdip02_Art16")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md)
- [Yollar Oluşturma ve Çizme](constructing-and-drawing-paths.md)
