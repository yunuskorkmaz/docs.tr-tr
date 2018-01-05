---
title: "GDI+'da Kalemler, Çizgiler ve Dikdörtgenler"
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
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7f21564c800dd960a96dfc024fa2cccc6b27780f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="pens-lines-and-rectangles-in-gdi"></a>GDI+'da Kalemler, Çizgiler ve Dikdörtgenler
Satırıyla çizmek için [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] oluşturmak gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesne gerçekten çizimi yapmak yöntemler sağlar ve <xref:System.Drawing.Pen> nesnesi çizgi rengini, genişliğini ve stil gibi özniteliklerini depolar.  
  
## <a name="drawing-a-line"></a>Bir çizgi çizme  
 Bir çizgi çizmek için çağrı <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi <xref:System.Drawing.Graphics> nesnesi. <xref:System.Drawing.Pen> Nesne bağımsız değişkenlerinden biri olarak geçirilir <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi. Aşağıdaki örnekte bir satırı (4, 2) noktasından (12, 6) noktasına çizilmiştir:  
  
 [!code-csharp[LinesCurvesAndShapes#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#41)]
 [!code-vb[LinesCurvesAndShapes#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#41)]  
  
 <xref:System.Drawing.Graphics.DrawLine%2A>Aşırı yüklenmiş bir yöntemi <xref:System.Drawing.Graphics> sağladığınız, bağımsız değişkenlerle çeşitli yollardan olduklarından sınıfı. Örneğin, iki oluşturabileceğiniz <xref:System.Drawing.Point> nesneleri ve geçişi <xref:System.Drawing.Point> nesneleri bağımsız değişken olarak <xref:System.Drawing.Graphics.DrawLine%2A> yöntemi:  
  
 [!code-csharp[LinesCurvesAndShapes#42](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#42)]
 [!code-vb[LinesCurvesAndShapes#42](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#42)]  
  
## <a name="constructing-a-pen"></a>Kalem oluşturma  
 Oluşturduğunuz zaman, belirli öznitelikleri belirtebilirsiniz bir <xref:System.Drawing.Pen> nesnesi. Örneğin, bir `Pen` oluşturucusu, renk ve genişlik belirtmenize olanak sağlar. Aşağıdaki örnek mavi bir çizgi genişliği 2 çizer (0, 0) için (60, 30):  
  
 [!code-csharp[LinesCurvesAndShapes#43](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#43)]
 [!code-vb[LinesCurvesAndShapes#43](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#43)]  
  
## <a name="dashed-lines-and-line-caps"></a>Kesikli satırları ve satır Caps  
 <xref:System.Drawing.Pen> Nesneyi de kullanıma sunan özellikleri gibi <xref:System.Drawing.Pen.DashStyle%2A>, satırın özelliklerini belirtmek için kullanabilirsiniz. Aşağıdaki örnek bir kesikli çizgi çizer (100, 50) için (300, 80):  
  
 [!code-csharp[LinesCurvesAndShapes#44](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#44)]
 [!code-vb[LinesCurvesAndShapes#44](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#44)]  
  
 Özelliklerini kullanabilirsiniz <xref:System.Drawing.Pen> nesne pek çok daha fazla çizgi özniteliklerini ayarlayın. <xref:System.Drawing.Pen.StartCap%2A> Ve <xref:System.Drawing.Pen.EndCap%2A> özellikleri satır uçlarından görünümünü belirtin; düz, kare, yuvarlatılmış, üçgen, uçları olabilir veya özel bir şekli. <xref:System.Drawing.Pen.LineJoin%2A> Özelliği bağlı çizgilere (keskin köşeleri ile birleştirilen) gönye, Eğimli, yuvarlatılmış veya kırpılmış olup olmadığını belirtmenize olanak sağlar. Aşağıdaki çizimde çeşitli cap ve birleştirme stilleri çizgilerle gösterilir.  
  
 ![Satırları](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art04.gif "Aboutgdip02_art04")  
  
## <a name="drawing-a-rectangle"></a>Dikdörtgene çizme  
 İle dikdörtgenler çizme [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] satırlar çizme için benzer. Dikdörtgen çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne ve <xref:System.Drawing.Pen> nesne. <xref:System.Drawing.Graphics> Nesnesi sağlar bir <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi ve <xref:System.Drawing.Pen> nesnesi çizgi genişliğini ve renk gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Nesne bağımsız değişkenlerinden biri olarak geçirilir <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi. Aşağıdaki örnek, sol üst köşede bir dikdörtgen çizer (100, 50), bir 80 genişliği ve yüksekliği 40 bir:  
  
 [!code-csharp[LinesCurvesAndShapes#45](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#45)]
 [!code-vb[LinesCurvesAndShapes#45](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#45)]  
  
 <xref:System.Drawing.Graphics.DrawRectangle%2A>Aşırı yüklenmiş bir yöntemi <xref:System.Drawing.Graphics> sağladığınız, bağımsız değişkenlerle çeşitli yollardan olduklarından sınıfı. Örneğin, oluşturabileceğiniz bir <xref:System.Drawing.Rectangle> nesne ve geçirin <xref:System.Drawing.Rectangle> nesnesinin <xref:System.Drawing.Graphics.DrawRectangle%2A> yöntemi bağımsız değişken olarak:  
  
 [!code-csharp[LinesCurvesAndShapes#46](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#46)]
 [!code-vb[LinesCurvesAndShapes#46](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#46)]  
  
 A <xref:System.Drawing.Rectangle> nesnesi yöntemlerini ve özelliklerini düzenleme ve dikdörtgen hakkında bilgi toplanıyor sahiptir. Örneğin, <xref:System.Drawing.Rectangle.Inflate%2A> ve <xref:System.Drawing.Rectangle.Offset%2A> yöntemleri boyutunu ve konumunu dikdörtgenin değiştirin. <xref:System.Drawing.Rectangle.IntersectsWith%2A> Yöntemi bildirir olup dikdörtgen başka kesiştiğinden dikdörtgen, verilen ve <xref:System.Drawing.Rectangle.Contains%2A> yöntemi söyler, verilen bir noktaya dikdörtgende olup olmadığı.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 <xref:System.Drawing.Rectangle?displayProperty=nameWithType>  
 [Nasıl yapılır: Kalem Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)  
 [Nasıl yapılır: Bir Windows Formunda Çizgi Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-a-line-on-a-windows-form.md)  
 [Nasıl yapılır: Ana Hatlı Şekil Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-an-outlined-shape.md)
