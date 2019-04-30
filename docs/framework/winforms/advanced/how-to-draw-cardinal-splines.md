---
title: 'Nasıl yapılır: Ana Eğriler Çizme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cardinal splines [Windows Forms], drawing
- drawing [Windows Forms], cardinal splines
- graphics [Windows Forms], cardinal splines
ms.assetid: a4a41e80-4461-4b47-b6bd-2c5e68881994
ms.openlocfilehash: 2f03177bf97936a2ca9558972d4d82fa3e07463c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61703743"
---
# <a name="how-to-draw-cardinal-splines"></a>Nasıl yapılır: Ana Eğriler Çizme
Kardinal eğri sorunsuz bir şekilde belirli bir nokta kümesi geçen bir eğri ' dir. Kardinal eğri çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesnesi ve bir dizi noktası adresini geçirmek <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi.  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>Zil şeklinde bir Kardinal eğri çizme  
  
- Aşağıdaki örnek zil şeklinde ve beş belirlenen noktalara geçirmeden bir Kardinal eğrisi çizer. Eğriyi ve beş noktaları aşağıda gösterilmiştir.  
  
     ![Zil şeklinde bir Kardinal eğri gösteren diyagram.](./media/how-to-draw-cardinal-splines/bell-shaped-cardinal-spline.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>Bir kapalı Kardinal eğri çizme  
  
- Kullanım <xref:System.Drawing.Graphics.DrawClosedCurve%2A> yöntemi <xref:System.Drawing.Graphics> bir kapalı Kardinal eğri çizmek için sınıf. Kapalı Kardinal eğri, eğrinin dizideki son noktası ile devam eder ve dizideki ilk noktasıyla bağlanır. Aşağıdaki örnek, altı belirlenen noktalara geçen bir kapalı Kardinal eğri çizer. Kapalı eğri altı noktaları ile birlikte aşağıda gösterilmiştir:  
  
 ![Bir kapalı Kardinal eğri gösteren diyagram.](./media/how-to-draw-cardinal-splines/closed-cardinal-spine.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>Kardinal eğri bSon değiştirme  
  
- Kardinal eğri bends gerilimi değişkenine geçirerek değiştirecek <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi. Aşağıdaki örnek, aynı dizi noktaları aracılığıyla geçen üç ana Eğriler çizer. Aşağıdaki çizim üç eğrileri gerilimi değerleriyle birlikte gösterir. Gerilimi 0 olduğunda noktaları düz satırlarla bağlı olduğunu unutmayın.  
  
 ![Üç ana Eğriler gösteren diyagram.](./media/how-to-draw-cardinal-splines/three-cardinal-splines.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde, Windows Forms ile kullanılmak üzere tasarlanmıştır ve gerektirdikleri <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Eğriler Oluşturma ve Çizme](constructing-and-drawing-curves.md)
