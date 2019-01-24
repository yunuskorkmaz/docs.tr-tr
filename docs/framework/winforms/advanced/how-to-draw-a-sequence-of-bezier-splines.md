---
title: 'Nasıl yapılır: Çizim, bir sıra B&#233;zier eğrileri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 45e56113334be4c384ef6f615d3062ed7f098ad1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572896"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a>Nasıl yapılır: Çizim, bir sıra B&#233;zier eğrileri
Kullanabileceğiniz <xref:System.Drawing.Graphics.DrawBeziers%2A> yöntemi <xref:System.Drawing.Graphics> dizisini çizmek için sınıf Bézier eğrileri bağlı.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek iki bağlı Bézier eğrileri oluşan bir eğrisi çizer. Uç nokta ilk Bézier eğri ikinci Bézier eğri başlangıç noktasıdır.  
  
 Bağlı eğrileri yedi noktaları ile birlikte aşağıda gösterilmiştir.  
  
 ![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Windows Forms’da Grafikler ve Çizim](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [GDI+'daki Bézier Eğrileri](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)
- [Eğriler Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
