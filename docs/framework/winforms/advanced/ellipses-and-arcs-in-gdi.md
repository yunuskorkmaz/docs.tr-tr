---
title: GDI+'da Elipsler ve Yaylar
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
- arcs
- GDI+, arcs
- drawing [Windows Forms], ellipses
- GDI+, ellipses
- ellipses
- drawing [Windows Forms], arcs
ms.assetid: 34f35133-a835-4ca4-81f6-0dfedee8b683
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebeae1d076a0ebcf36d52dee1af0c0ad5f04fdf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="ellipses-and-arcs-in-gdi"></a>GDI+'da Elipsler ve Yaylar
Elipsler ve yaylar kullanarak kolayca çizebilirsiniz <xref:System.Drawing.Graphics.DrawEllipse%2A> ve <xref:System.Drawing.Graphics.DrawArc%2A> yöntemlerinin <xref:System.Drawing.Graphics> sınıfı.  
  
## <a name="drawing-an-ellipse"></a>Elips çizme  
 Elips çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi genişlik ve üç nokta işlemek için kullanılan çizginin rengini gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Nesne bağımsız değişkenlerinden biri olarak geçirilir <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi. Kalan bağımsız değişkenleri geçirilen <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi elips için sınırlayıcı dikdörtgenini belirtin. Elips sınırlayıcı dikdörtgenini birlikte aşağıda gösterilmiştir.  
  
 ![Elipsler ve yaylar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art05.gif "Aboutgdip02_art05")  
  
 Aşağıdaki örnekte bir elips çizer; 80, 40 yüksekliğini ve sol üst köşesindeki genişliğini sınırlayıcı dikdörtgenini sahiptir (100, 50):  
  
 [!code-csharp[LinesCurvesAndShapes#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#51)]
 [!code-vb[LinesCurvesAndShapes#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#51)]  
  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>Aşırı yüklenmiş bir yöntemi <xref:System.Drawing.Graphics> sağladığınız, bağımsız değişkenlerle çeşitli yollardan olduklarından sınıfı. Örneğin, oluşturabileceğiniz bir <xref:System.Drawing.Rectangle> ve geçirin <xref:System.Drawing.Rectangle> için <xref:System.Drawing.Graphics.DrawEllipse%2A> yöntemi bağımsız değişken olarak:  
  
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
 [Çizgiler, eğriler ve şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: çizim için grafik nesneleri oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Nasıl yapılır: Kalem oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Nasıl yapılır: Anahatlı şekil çizme](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
