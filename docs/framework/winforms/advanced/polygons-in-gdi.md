---
title: GDI+'daki Çokgenler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- polygons
- drawing [Windows Forms], polygons
- GDI+, polygons
ms.assetid: a72213d2-d69a-4c2b-a75c-be7b20390c13
ms.openlocfilehash: cffbee5f73b9fe92e2f1f3c7eff2f2336d9123a5
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710088"
---
# <a name="polygons-in-gdi"></a>GDI+'daki Çokgenler
Bir çokgenin üç veya daha fazla düz kenarlar ile kapalı şekildir. Örneğin, üç kenarı sahip bir çokgenin bir üçgen olan dört tarafında sahip bir çokgenin dikdörtgen şeklinde ve beş yüz sahip bir çokgenin bir Beşgene olduğu. Aşağıdaki resimde, birkaç çokgenler gösterilmektedir.  
  
 ![Polygons](./media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Bir çokgenin çizme  
 Bir çokgenin çizmek için ihtiyacınız bir <xref:System.Drawing.Graphics> nesnesi bir <xref:System.Drawing.Pen> nesnesi ve bir dizi <xref:System.Drawing.Point> (veya <xref:System.Drawing.PointF>) nesneleri. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi. <xref:System.Drawing.Pen> Nesnesini depolar genişlik ve Çokgen ve dizi oluşturmak için kullanılan çizginin rengi gibi öznitelikleri <xref:System.Drawing.Point> nesneleri tarafından düz çizgiler bağlanması noktalarını depolar. <xref:System.Drawing.Pen> Nesne ve dizi <xref:System.Drawing.Point> nesneleri bağımsız değişkenleri olarak geçirilir <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi. Aşağıdaki örnek, üç taraflı bir çokgen çizer. Yalnızca üç noktalar olduğunu unutmayın `myPointArray`: (0, 0), (50, 30) ve (30, 60). <xref:System.Drawing.Graphics.DrawPolygon%2A> Yöntemi otomatik olarak bir çizgi çizerek Çokgen kapatır (30, 60) tekrar için başlangıç noktası (0, 0).  
  
 [!code-csharp[LinesCurvesAndShapes#111](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 Çokgen aşağıda gösterilmiştir.  
  
 ![Polygon](./media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Nasıl yapılır: Kalem oluşturma](how-to-create-a-pen.md)
