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
ms.openlocfilehash: 3ad06eb28e1d8e6b5d5f4a77e545f174d8a68d9b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525066"
---
# <a name="how-to-draw-cardinal-splines"></a>Nasıl yapılır: Ana Eğriler Çizme
Kardinal eğri sorunsuz verilen kümesini noktaları geçirir bir eğri ' dir. Kardinal eğri çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesne ve bir dizi noktalarına adresini geçirin <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi.  
  
### <a name="drawing-a-bell-shaped-cardinal-spline"></a>Zil şeklinde Kardinal eğrisi çizme  
  
-   Aşağıdaki örnek zil şeklinde ve beş belirlenen noktalara geçirmeden bir Kardinal eğri çizer. Aşağıdaki çizimde eğri ve beş noktalarını gösterir.  
  
     ![Kardinal eğri](../../../../docs/framework/winforms/advanced/media/cardinalspline1.png "CardinalSpline1")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#21)]  
  
### <a name="drawing-a-closed-cardinal-spline"></a>Kapalı Kardinal eğri çizme  
  
-   Kullanım <xref:System.Drawing.Graphics.DrawClosedCurve%2A> yöntemi <xref:System.Drawing.Graphics> kapalı Kardinal eğri çizmek için sınıf. Kapalı Kardinal eğri eğri dizideki son noktası ile devam eder ve dizinin ilk noktasıyla bağlanır. Aşağıdaki örnekte, altı belirlenen noktalara geçirir kapalı bir Kardinal eğri çizilmiştir. Kapalı eğri altı noktaları ile birlikte aşağıda gösterilmiştir.  
  
 ![Kardinal eğri](../../../../docs/framework/winforms/advanced/media/cardinalspline1a.png "CardinalSpline1A")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#22)]  
  
### <a name="changing-the-bend-of-a-cardinal-spline"></a>Kardinal eğri bSon değiştirme  
  
-   Kardinal eğri bends gerilim bağımsız değişkeni geçirerek şeklini değiştirmenize <xref:System.Drawing.Graphics.DrawCurve%2A> yöntemi. Aşağıdaki örnekte noktaları aynı dizi ile geçmesi üç ana Eğriler çizilmiştir. Aşağıdaki çizim üç eğrileri gerilim değerleriyle birlikte göstermektedir. Gerilim 0 olduğunda noktaları düz çizgilerle bağlandığını unutmayın.  
  
 ![Kardinal eğri](../../../../docs/framework/winforms/advanced/media/cardinalspline2.png "CardinalSpline2")  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#23)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
 Önceki örneklerde Windows Forms ile kullanılmak üzere tasarlanmıştır ve ihtiyaç <xref:System.Windows.Forms.PaintEventArgs> `e`, parametre olarak olduğu <xref:System.Windows.Forms.Control.Paint> olay işleyicisi.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Eğriler Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
