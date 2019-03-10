---
title: B&#233;zier GDI +'daki eğrileri
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: 7648f7f9da72abea4bfc87603eea290614294eff
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707267"
---
# <a name="b233zier-splines-in-gdi"></a>B&#233;zier GDI +'daki eğrileri
Dört noktası tarafından belirtilen eğri Bézier eğri olduğu: iki uç noktaları (p1 ve p2) ve iki denetim noktaları (c1 ve c2). Eğriyi, başlar p1 ve p2 sona erer. Eğri denetim noktaları üzerinden geçmez, ancak denetim noktaları belirli yönde eğri çekmek ve bends eğrinin şeklini etkileyen mıknatıs davranır. Bézier eğri denetim noktalarını ve uç noktaları ile birlikte aşağıda gösterilmiştir.  
  
 ![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 Eğriyi, p1 başlatır ve kontrol noktası c1 doğru taşır. Eğim satırına kıvrımın p1, p1 c1 için çizgi ' dir. Uç nokta p2 Eğim satırında c2 p2 için çizgi ' dir.  
  
## <a name="drawing-bzier-splines"></a>Çizim Bézier eğrileri  
 Örneği ihtiyacınız Bézier eğri çizmek için <xref:System.Drawing.Graphics> sınıfı ve <xref:System.Drawing.Pen>. Örneğini <xref:System.Drawing.Graphics> sağlar sınıfını <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi ve <xref:System.Drawing.Pen> genişlik ve eğri işlemek için kullanılan çizginin rengi gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Bir bağımsız değişken olarak geçirilen <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi. Kalan bağımsız değişkenleri geçirilen <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi olan uç noktaları ve denetim noktaları. Aşağıdaki örnek, başlangıç noktası (0, 0) ile bir Bézier eğrisi çizer kontrol noktaları (40, 20) ve (80, 150) ve bitiş noktası (100, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 Eğri denetim noktalarını ve Eğim satırlarını aşağıda gösterilmiştir.  
  
 ![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 Bézier eğrileri Pierre Bézier tarafından otomotiv sektöründe tasarımı için ilk olarak geliştirilmiştir. Bunlar, bilgisayar destekli tasarım birçok türde kullanışlı olması için beri kanıtlanmış ve yazı tipleri anahatlarını tanımlamak için kullanılır. Şekiller, bazıları aşağıda gösterilen çeşitli Bézier eğrileri sağlayabilir.  
  
 ![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Eğriler Oluşturma ve Çizme](constructing-and-drawing-curves.md)
- [Nasıl yapılır: Çizim için grafik nesneleri oluşturma](how-to-create-graphics-objects-for-drawing.md)
- [Nasıl yapılır: Kalem oluşturma](how-to-create-a-pen.md)
