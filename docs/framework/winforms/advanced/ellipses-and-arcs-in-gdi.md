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
ms.openlocfilehash: 6835127d03f984bda8a95cf5b9ca9798122de804
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522115"
---
# <a name="ellipses-and-arcs-in-gdi"></a>GDI+'da Elipsler ve Yaylar
Elipsler ve yaylar kullanarak kolayca çizebilirsiniz <xref:System.Drawing.Graphics.DrawEllipse%2A> ve <xref:System.Drawing.Graphics.DrawArc%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.  
  
## <a name="drawing-an-ellipse"></a>Elips çizme  
 Elips çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi genişlik ve üç nokta işlemek için kullanılan çizginin rengini gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Nesne bağımsız değişkenlerinden biri olarak geçirilir <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi. Kalan bağımsız değişkenleri geçirilen <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi elips için sınırlayıcı dikdörtgenini belirtin. Elips sınırlayıcı dikdörtgenini birlikte aşağıda gösterilmiştir.  
  
 ![Elipsler ve yaylar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 Aşağıdaki örnekte bir elips çizer; 80, 40 yüksekliğini ve sol üst köşesindeki genişliğini sınırlayıcı dikdörtgenini sahiptir (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A> Aşırı yüklenmiş bir yöntemi <xref:System.Drawing.Graphics> sağladığınız, bağımsız değişkenlerle çeşitli yollardan olduklarından sınıfı. Örneğin, oluşturabileceğiniz bir <xref:System.Drawing.Rectangle> ve geçirin <xref:System.Drawing.Rectangle> için <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi bağımsız değişken olarak:  
  
 [!code-csharp[LinesCurvesAndShapes#52](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#52)]
 [!code-vb[LinesCurvesAndShapes#52](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#52)]  
  
## <a name="drawing-an-arc"></a>Yay çizme  
 Yayı elips bölümüdür. Yay çizmek için arama <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi <xref:System.Drawing.Graphics> sınıfı. Parametreleri <xref:System.Drawing.Graphics.DrawArc%2A> yöntemi aynıdır parametrelerinin <xref:System.Drawing.Graphics.DrawEllipse%2A> hariç yöntemi <xref:System.Drawing.Graphics.DrawArc%2A> Başlangıç açısı ve tarama açısı gerektirir. Aşağıdaki örnekte bir yay 30 derece Başlangıç açısı ve tarama açısı 180 derece çizilmiştir:  
  
 [!code-csharp[LinesCurvesAndShapes#53](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#53)]
 [!code-vb[LinesCurvesAndShapes#53](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#53)]  
  
 Aşağıdaki çizimde, arc, üç nokta ve sınırlayıcı dikdörtgenini gösterir.  
  
 ![Elipsler ve yaylar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art06.gif "Aboutgdip02_art06")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Nasıl yapılır: Kalem Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Nasıl yapılır: Ana Hatlı Şekil Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
