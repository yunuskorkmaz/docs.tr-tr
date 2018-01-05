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
ms.workload: dotnet
ms.openlocfilehash: 6d2eaf570190f85ca084e5a5ab5d1bee1be56871
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
 [GDI+'daki Bézier Eğrileri](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [Nasıl yapılır: Bir Sıra Bézier Eğrisi Çizme](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
