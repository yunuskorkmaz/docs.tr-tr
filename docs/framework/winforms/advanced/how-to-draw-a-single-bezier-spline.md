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
ms.openlocfilehash: 6fc4e12bb7532019a0571095263b5447e4b0d1ed
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702522"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a>Nasıl yapılır: Tek bir B çizmek&#233;zier eğri
Bézier eğri dört noktaları tarafından tanımlanır: bir başlangıç noktası, iki denetim noktalarını ve uç nokta.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, başlangıç noktası (10, 100) ve (200, 100) uç noktası olan bir Bézier eğrisi çizer. Denetim olan (100, 10) ve (150, 150) işaret eder.  
  
 Sonuçta elde edilen Bézier eğri, başlangıç noktası, denetim noktalarını ve uç nokta ile birlikte aşağıda gösterilmiştir. Çizimde, dört noktası düz çizgiler ile bağlanarak oluşturulmuş bir Çokgen eğri'nın dışbükey Kabuk da gösterilmektedir.  
  
 ![Bezier Spline](./media/bezierspline1.png "BezierSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Yukarıdaki örnekte, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirir <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [GDI+'daki Bézier Eğrileri](bezier-splines-in-gdi.md)
- [Nasıl yapılır: Bir dizi Bézier eğrileri çizme](how-to-draw-a-sequence-of-bezier-splines.md)
