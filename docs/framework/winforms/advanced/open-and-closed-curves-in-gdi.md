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
ms.openlocfilehash: 47f420184ac384ab11054d1cc3e767ab7f618234
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="open-and-closed-curves-in-gdi"></a>GDI+'da Açık ve Kapalı Eğriler
İki eğri aşağıda gösterilmiştir: bir açık ve bir kapalı.  
  
 ![Açık ve kapalı Eğriler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art24.gif "Aboutgdip02_art24")  
  
## <a name="managed-interface-for-curves"></a>Eğriler için yönetilen arabirimi  
 Kapalı Eğriler bir iç varsa ve bu nedenle fırça ile doldurulabilir. <xref:System.Drawing.Graphics> Sınıfını [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] kapalı şekiller ve eğrilerle doldurmak için aşağıdaki yöntemleri sağlar: <xref:System.Drawing.Graphics.FillRectangle%2A>, <xref:System.Drawing.Graphics.FillEllipse%2A>, <xref:System.Drawing.Graphics.FillPie%2A>, <xref:System.Drawing.Graphics.FillPolygon%2A>, <xref:System.Drawing.Graphics.FillClosedCurve%2A>, <xref:System.Drawing.Graphics.FillPath%2A>, ve <xref:System.Drawing.Graphics.FillRegion%2A>. Aşağıdaki yöntemlerden birini çağrısı zaman, belirli fırça türlerinden birini geçmesi gerekir (<xref:System.Drawing.SolidBrush>, <xref:System.Drawing.Drawing2D.HatchBrush>, <xref:System.Drawing.TextureBrush>, <xref:System.Drawing.Drawing2D.LinearGradientBrush>, veya <xref:System.Drawing.Drawing2D.PathGradientBrush>) bağımsız değişken olarak.  
  
 <xref:System.Drawing.Graphics.FillPie%2A> Bir yardımcı yöntemdir <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi. Gibi <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi bir kısmı bir elips anahat çizer <xref:System.Drawing.Graphics.FillPie%2A> yöntemi elips iç kısmını doldurur. Aşağıdaki örnek, bir yay çizer ve karşılık gelen elipsin iç kısmını doldurur:  
  
 [!code-csharp[LinesCurvesAndShapes#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#21)]
 [!code-vb[LinesCurvesAndShapes#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#21)]  
  
 Yayı ve dolgulu pasta aşağıda gösterilmektedir.  
  
 ![Açık ve kapalı Eğriler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art25.gif "Aboutgdip02_art25")  
  
 <xref:System.Drawing.Graphics.FillClosedCurve%2A> Bir yardımcı yöntemdir <xref:System.Drawing.Graphics.DrawClosedCurve%2A> yöntemi. Her iki yöntem için başlangıç noktası bitiş noktasına bağlanarak eğri otomatik olarak kapanır. Aşağıdaki örnek geçtiği bir eğri çizer (0, 0), (60, 20) ve (40, 50). Ardından, bağlanarak otomatik olarak eğri kapatıldıktan (40, 50) (0, 0), başlangıç noktası için ve iç tam renkle doldurulur.  
  
 [!code-csharp[LinesCurvesAndShapes#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#22)]
 [!code-vb[LinesCurvesAndShapes#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#22)]  
  
 <xref:System.Drawing.Graphics.FillPath%2A> Yöntemi bir yolu ayrı parçasını evin içindekiler doldurur. Bir yol parçasını kapalı eğri veya şekil, form değil, <xref:System.Drawing.Graphics.FillPath%2A> yöntemi otomatik olarak doldurma önce yolun parçasının kapatır. Aşağıdaki örnek, çizer ve yay, Kardinal eğri, bir dize ve bir pasta oluşan bir yol doldurur:  
  
 [!code-csharp[LinesCurvesAndShapes#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#23)]
 [!code-vb[LinesCurvesAndShapes#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#23)]  
  
 Aşağıdaki çizimde ile ve düz dolgu olmadan yolunu gösterir. Metin dizesindeki özetlenen, ancak, bunun doldurulmamış olduğunu Not <xref:System.Drawing.Graphics.DrawPath%2A> yöntemi. Bu <xref:System.Drawing.Graphics.FillPath%2A> dizesindeki karakterlerin evin içindekiler boyar yöntemi.  
  
 ![Bir yol dizesindeki](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art26.gif "Aboutgdip02_art26")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Yollar Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
