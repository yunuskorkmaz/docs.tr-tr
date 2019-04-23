---
title: GDI+'da Açık ve Kapalı Eğriler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- curves [Windows Forms], filling
- GDI+, curves
- curves [Windows Forms], drawing
- curves
ms.assetid: 08d2cc9a-dc9d-4eed-bcbb-2c8e2ca5d3ae
ms.openlocfilehash: 33a8954296a7e63637ad5e210fb30fba1a3fdd53
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59165119"
---
# <a name="open-and-closed-curves-in-gdi"></a>GDI+'da Açık ve Kapalı Eğriler
İki eğriye aşağıda gösterilmiştir: bir açık ve biri kapalı.  
  
 ![Açık ve kapalı Eğriler](./media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Eğrileri yönetilen arabirimi  
 Kapalı Eğriler bir iç sahip ve bu nedenle bir fırça ile doldurulur. <xref:System.Drawing.Graphics> Sınıfını [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kapalı şekiller ve eğriler doldurmak için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, ve <xref:System.Drawing.Graphics.FillRegion%2A>. Aşağıdaki yöntemlerden birini çağırma olduğunda, belirli bir fırça türlerinden birini geçmelidir (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, veya <xref:System.Drawing.Drawing2D.PathGradientBrush>) bağımsız değişken olarak.  
  
 <xref:System.Drawing.Graphics.FillPie%2A> İçin bir yardımcı yöntemdir <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi. Gibi <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi çizen bir bölümü bir elips ana hat <xref:System.Drawing.Graphics.FillPie%2A> yöntemi, bir elips iç kısmını doldurur. Aşağıdaki örnek, bir yay çizer ve karşılık gelen koordinatlarıyla iç bölümünün doldurur:  
  
 [!code-csharp[LinesCurvesAndShapes#21](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 Yayı ve dolu pasta aşağıda gösterilmiştir.  
  
 ![Açık ve kapalı Eğriler](./media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> İçin bir yardımcı yöntemdir <xref:System.Drawing.Graphics.DrawClosedCurve%2A> yöntemi. Her iki yöntem için başlangıç noktası bitiş noktasına bağlanarak eğri otomatik olarak kapanır. Aşağıdaki örnek geçtiği bir eğrisi çizer (0, 0), (60, 20) ve (40, 50). Daha sonra bağlanarak otomatik olarak eğri kapatıldıktan (40, 50) için başlangıç noktası (0, 0) ve iç düz renk ile doldurulur.  
  
 [!code-csharp[LinesCurvesAndShapes#22](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> Yöntemi evin içindekiler ayrı bir yol parçasını doldurur. Bir yol parçasının kapalı eğri veya şekil değil biçimlendiriyorsa <xref:System.Drawing.Graphics.FillPath%2A> yöntemi otomatik olarak doldurma önce yolu olan İnceleyenleri kapatır. Aşağıdaki örnek, çizer ve Yayı Kardinal eğri, bir dize ve bir pasta oluşan bir yol doldurur:  
  
 [!code-csharp[LinesCurvesAndShapes#23](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 Aşağıdaki çizim olan ve olmayan tek renk dolgu yolunu gösterir. Metin dizesindeki özetlenen olmakla birlikte, bunun doldurulmamış olduğunu Not <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi. Bu <xref:System.Drawing.Graphics.FillPath%2A> evin içindekiler dizedeki karakterlerin boyar yöntemi.  
  
 ![Bir yol dizesindeki](./media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Point?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md)
- [Yollar Oluşturma ve Çizme](constructing-and-drawing-paths.md)
