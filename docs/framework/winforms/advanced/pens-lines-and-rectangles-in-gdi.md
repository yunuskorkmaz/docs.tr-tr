---
title: GDI+'da Kalemler, Çizgiler ve Dikdörtgenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines
- GDI+, lines
- drawing [Windows Forms], rectangles
- rectangles
- drawing [Windows Forms], lines
- GDI+, pens
- examples [Windows Forms], drawing lines and shapes
- examples [Windows Forms], pens
- GDI+, rectangles
- examples [Windows Forms], GDI+
- lines [Windows Forms], dashed
ms.assetid: 30b25aae-e3eb-4479-bdb8-187cf651fc84
ms.openlocfilehash: 91f41fb4acf5ec174bd76498a70aed3dcda076f9
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57705751"
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>GDI+'da Kalemler, Çizgiler ve Dikdörtgenler
İle çizgi çizmek için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] oluşturmak gereken bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesne çizim yapan yöntemler sağlar ve <xref:System.Drawing.Pen> nesnesi gibi çizgi rengini, genişliğini ve stili özniteliklerini depolar.  
  
## <a name="drawing-a-line"></a>Bir çizgi çizme  
 Bir çizgi çizmek için çağrı <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> nesne. <xref:System.Drawing.Pen> Bir bağımsız değişken olarak geçirilen nesne <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi. Aşağıdaki örnek, (4, 2) noktadan noktaya (12, 6) bir çizgi çizer:  
  
 [!code-csharp[LinesCurvesAndShapes#41](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A> Aşırı yüklenmiş bir yöntemidir <xref:System.Drawing.Graphics> çeşitli yolları sağladığınız bu bağımsız değişkenlerle olduklarından sınıfı. Örneğin, iki oluşturabilirsiniz <xref:System.Drawing.Point> nesneleri ve pass <xref:System.Drawing.Point> bağımsız değişkenleri olarak nesneleri <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi:  
  
 [!code-csharp[LinesCurvesAndShapes#42](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Kalem oluşturma  
 Oluşturduğunuzda, belirli öznitelikleri belirtebileceğiniz bir <xref:System.Drawing.Pen> nesne. Örneğin, bir `Pen` oluşturucusu, renk ve genişlik belirtmenize olanak sağlar. Aşağıdaki örnek 2 genişliğini mavi bir çizgi çizer (0, 0) için (60, 30):  
  
 [!code-csharp[LinesCurvesAndShapes#43](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Kesik çizgi ve satır Caps  
 <xref:System.Drawing.Pen> Nesne de sunan özellikler gibi <xref:System.Drawing.Pen.DashStyle%2A>, satırın özelliklerini belirtmek için kullanabilirsiniz. Aşağıdaki örnek kesikli bir çizgi çizer (100, 50) için (300, 80):  
  
 [!code-csharp[LinesCurvesAndShapes#44](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Özelliklerini kullanabilirsiniz <xref:System.Drawing.Pen> nesne çok daha fazla satır özniteliklerini ayarlayın. <xref:System.Drawing.Pen.StartCap%2A> Ve <xref:System.Drawing.Pen.EndCap%2A> özellikler çizginin uçlarını görünümünü belirtin; uçları olabilir düz, kare, yuvarlak, üçgen, ya da özel bir şekil. <xref:System.Drawing.Pen.LineJoin%2A> Özelliği, bağlı çizgiler (keskin köşeleri ile birleştirilmiş) gönye Eğimli, yuvarlak veya kırpılarak olup olmadığını belirlemenize olanak sağlar. Aşağıdaki çizimde, çeşitli büyük harf ve birleştirme stilleri sahip satırları gösterilir.  
  
 ![Satırları](./media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Dikdörtgen çizme  
 İle dikdörtgenler çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] satırlar çizme için benzer. Bir dikdörtgen çizmek için gereken bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlayan bir <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesneyi çizgi genişliği ve rengine gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Bir bağımsız değişken olarak geçirilen nesne <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi. Aşağıdaki örnek, sol üst köşesinde bir dikdörtgen çizer (100, 50) bir 80 genişlik ve yükseklik 40'a:  
  
 [!code-csharp[LinesCurvesAndShapes#45](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A> Aşırı yüklenmiş bir yöntemidir <xref:System.Drawing.Graphics> çeşitli yolları sağladığınız bu bağımsız değişkenlerle olduklarından sınıfı. Örneğin, oluşturun bir <xref:System.Drawing.Rectangle> nesne ve geçirin <xref:System.Drawing.Rectangle> nesnesini <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bağımsız değişken olarak:  
  
 [!code-csharp[LinesCurvesAndShapes#46](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A <xref:System.Drawing.Rectangle> nesnesi yöntemlerini ve özelliklerini düzenleme ve dikdörtgen hakkında bilgileri toplamak için sahiptir. Örneğin, <xref:System.Drawing.Rectangle.Inflate%2A> ve <xref:System.Drawing.Rectangle.Offset%2A> yöntemleri, boyutunu ve konumunu dikdörtgenin değiştirin. <xref:System.Drawing.Rectangle.IntersectsWith%2A> Yöntemi bildirir olup dikdörtgen başka kesişip dikdörtgen, verilen ve <xref:System.Drawing.Rectangle.Contains%2A> yöntemi söyler, belirli bir noktaya dikdörtgen içinde olup.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- <xref:System.Drawing.Rectangle?displayProperty=nameWithType>
- [Nasıl yapılır: Kalem oluşturma](how-to-create-a-pen.md)
- [Nasıl yapılır: Bir Windows formunda çizgi çizme](how-to-draw-a-line-on-a-windows-form.md)
- [Nasıl yapılır: Anahatlı şekil çizme](how-to-draw-an-outlined-shape.md)
