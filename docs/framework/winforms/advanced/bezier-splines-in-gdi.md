---
title: "B &#233; zier GDI +'daki eğrileri"
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
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cc06a81c879e6ebd50c4eb6a70590c28cc43f6e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="b233zier-splines-in-gdi"></a>B &#233; zier GDI +'daki eğrileri
Dört noktaları tarafından belirtilen bir eğri Bézier eğrisi olduğu: iki uç noktaları (p1 ve p2) ve iki denetim noktaları (c1 ve c2). Eğri p1 başlar ve p2 sona erer. Eğri denetim noktaları aracılığıyla vermeyen, ancak denetim noktaları eğri belirli yönde çekme ve eğri bends şekilde etkileyen mıknatıs davranacak. Aşağıdaki çizimde, kendi uç noktaları ve denetim noktalarının yanı sıra Bézier eğrisi gösterir.  
  
 ![Bezier eğrileri](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")  
  
 Eğriyi p1 başlatır ve denetim noktası c1 doğru taşır. Eğri p1 oluşturacak Eğim satırına p1 c1 için çizgi ' dir. Uç nokta p2 Eğim satırında c2 p2 için çizgi ' dir.  
  
## <a name="drawing-bzier-splines"></a>Bézier eğrisi çizme  
 Örneği ihtiyacınız Bézier eğrisi çizme için <xref:System.Drawing.Graphics> sınıfı ve bir <xref:System.Drawing.Pen>. Örneğinin <xref:System.Drawing.Graphics> SAX <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi ve <xref:System.Drawing.Pen> genişlik ve eğri işlemek için kullanılan çizginin rengini gibi özniteliklerini depolar. <xref:System.Drawing.Pen> Bağımsız değişkenlerinden biri olarak geçirilen <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi. Kalan bağımsız değişkenleri geçirilen <xref:System.Drawing.Graphics.DrawBezier%2A> yöntemi olan uç noktaları ve denetim noktaları. Aşağıdaki örnek, başlangıç noktası (0, 0) ile bir Bézier eğrisi çizer kontrol noktaları (40, 20) ve (80, 150) ve bitiş noktası (100, 10):  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 Aşağıdaki çizimde eğri, denetim noktaları ve iki Eğim çizgisi gösterir.  
  
 ![Bezier eğrileri](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")  
  
 Bézier eğrisi öğesini endüstri tasarımındaki Pierre Bézier tarafından ilk olarak geliştirilmiştir. Bunlar, birçok bilgisayar destekli tasarım türlerinde kullanışlı olması için beri kanıtlanmış ve yazı tipleri anahatları tanımlamak için de kullanılır. Bézier eğrileri bazıları aşağıdaki çizimde gösterilen şekiller, birçok farklı yol açabilir.  
  
 ![Yollar](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Eğriler Oluşturma ve Çizme](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [Nasıl yapılır: Çizim için Grafik Nesneleri Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Nasıl yapılır: Kalem Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
