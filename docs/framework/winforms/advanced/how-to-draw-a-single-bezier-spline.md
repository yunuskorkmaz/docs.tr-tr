---
title: 'Nasıl yapılır: Tek bir B çizmek&#233;zier eğri'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: ebb53e7df979a553ed4a44deba34345c9ecac772
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171684"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Nasıl yapılır: Tek bir B çizmek&#233;zier eğri
Bézier eğri dört noktaları tarafından tanımlanır: bir başlangıç noktası, iki denetim noktalarını ve uç nokta.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, başlangıç noktası (10, 100) ve (200, 100) uç noktası olan bir Bézier eğrisi çizer. Denetim olan (100, 10) ve (150, 150) işaret eder.  
  
 Sonuçta elde edilen Bézier eğri, başlangıç noktası, denetim noktalarını ve uç nokta ile birlikte aşağıda gösterilmiştir. Çizimde, dört noktası düz çizgiler ile bağlanarak oluşturulmuş bir Çokgen eğri'nın dışbükey Kabuk da gösterilmektedir.  
  
 ![Bezier eğrisi gösterimi.](./media/how-to-draw-a-single-bezier-spline/bezier-spline-illustration.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [GDI+ içinde Bézier Eğrileri](bezier-splines-in-gdi.md)
- [Nasıl yapılır: Bir Sıra Bézier Eğrisi Çizme](how-to-draw-a-sequence-of-bezier-splines.md)
