---
title: "Nasıl yapılır: çizim tek B &#233; zier eğri"
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
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0ebdba9e01824cc764a6ab759da049add180ba83
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Nasıl yapılır: çizim tek B &#233; zier eğri
Bir Bézier eğrisi dört noktaları tarafından tanımlanır: bir başlangıç noktası, iki denetim noktası ve bir uç nokta.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, başlangıç noktası (10, 100) ve (200, 100) uç noktası olan bir Bézier eğrisi çizer. Denetim noktalarını olan (100, 10) ve (150 150).  
  
 Sonuçta elde edilen bir Bézier eğrisi başlangıç noktasını, denetim noktaları ve uç nokta ile birlikte aşağıda gösterilmiştir. Çizimde de düz satırıyla dört noktası bağlanarak biçimlendirilmiş bir Çokgen eğri 's dışbükey hull gösterilmektedir.  
  
 ![Bezier eğrisi](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örnekte Windows Forms ile kullanılmak üzere tasarlanmış ve gerektirip <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics.DrawBezier%2A>  
 [GDI +'daki Bézier eğrileri](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Nasıl yapılır: bir sıra Bézier eğrisi çizme](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
