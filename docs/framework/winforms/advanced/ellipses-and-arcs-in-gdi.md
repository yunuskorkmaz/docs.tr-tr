---
title: GDI+'da Elipsler ve Yaylar
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
ms.openlocfilehash: 8bbc2eda6450128eac55576259880e83f07099ab
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61756656"
---
# <a name="ellipses-and-arcs-in-gdi"></a>GDI+'da Elipsler ve Yaylar
Elipsler ve yaylar kullanarak kolayca çizebilirsiniz <xref:System.Drawing.Graphics.DrawEllipse%2A> ve <xref:System.Drawing.Graphics.DrawArc%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.  
  
## <a name="drawing-an-ellipse"></a>Elips çizme  
 Elips çizin için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi ve bir <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi ve <xref:System.Drawing.Pen> nesneyi genişlik ve üç nokta işlemek için kullanılan çizginin rengi gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Bir bağımsız değişken olarak geçirilen nesne <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi. Kalan bağımsız değişkenleri geçirilen <xref:System.Drawing.Graphics.DrawEllipse%2A> elipsin dikdörtgen yöntemini belirtin. Elips, sınırlayıcı bir dikdörtgen ile birlikte aşağıda gösterilmiştir.  
  
 ![Elipsler ve yaylar](./media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 Aşağıdaki örnek, bir elips çizer; sınırlayıcı dikdörtgeni 80, 40 yüksekliğini ve bir sol üst köşesinde genişliğini sahip (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> Aşırı yüklenmiş bir yöntemidir <xref:System.Drawing.Graphics> çeşitli yolları sağladığınız bu bağımsız değişkenlerle olduklarından sınıfı. Örneğin, oluşturun bir <xref:System.Drawing.Rectangle> ve <xref:System.Drawing.Rectangle> için <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi bağımsız değişken olarak:  
  
 [!code-csharp[LinesCurvesAndShapes#52](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Yay çizme  
 Yay elips bölümüdür. Yay çizmenin için çağırırsınız <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Parametreleri <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi, aynı parametreleri olarak <xref:System.Drawing.Graphics.DrawEllipse%2A> hariç yöntemi <xref:System.Drawing.Graphics.DrawArc%2A> Başlangıç açısı ve tarama açısı gerektirir. Aşağıdaki örnek, bir Başlangıç açısı derece 30 ve 180 derece bir tarama açısı yay çizer:  
  
 [!code-csharp[LinesCurvesAndShapes#53](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 Aşağıdaki çizimde, arc, elips ve dikdörtgen gösterilir.  
  
 ![Elipsler ve yaylar](./media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md)
- [Nasıl yapılır: Kalem oluşturma](how-to-create-a-pen.md)
- [Nasıl yapılır: Anahatlı şekil çizme](how-to-draw-an-outlined-shape.md)
