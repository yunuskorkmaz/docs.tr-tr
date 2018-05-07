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
ms.openlocfilehash: 3ac6b9b651e65a45612cf2bd8ff17990c5cfba0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="polygons-in-gdi"></a>GDI+'daki Çokgenler
Çokgen üç veya daha fazla düz kenarlar ile kapalı bir Şekil ' dir. Örneğin, bir üçgen üç kenarı sahip bir çokgenin, bir Çokgen dört kenara dikdörtgen şeklinde ve beş kenara sahip bir çokgenin bir pentagon olduğu. Aşağıda birkaç çokgenler gösterilmektedir.  
  
 ![Çokgenler](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art07.gif "Aboutgdip02_art07")  
  
## <a name="drawing-a-polygon"></a>Çokgen çizme  
 Çokgen çizmek için size gereken bir <xref:System.Drawing.Graphics> nesne, bir <xref:System.Drawing.Pen> nesne ve bir dizi <xref:System.Drawing.Point> (veya <xref:System.Drawing.PointF>) nesneleri. <xref:System.Drawing.Graphics> Nesnesi sağlar <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi. <xref:System.Drawing.Pen> Nesne depolar genişlik ve Çokgen ve dizi oluşturmak için kullanılan çizginin rengini gibi öznitelikleri <xref:System.Drawing.Point> nesnelerini depolayan noktaları düz çizgilerle bağlanması gerekir. <xref:System.Drawing.Pen> Nesne ve bir dizi <xref:System.Drawing.Point> nesneleri bağımsız değişken olarak geçirilen <xref:System.Drawing.Graphics.DrawPolygon%2A> yöntemi. Aşağıdaki örnekte, üç taraflı çokgen çizer. Yalnızca üç noktaları olduğuna dikkat edin `myPointArray`: (0, 0), (50, 30) ve (30, 60). <xref:System.Drawing.Graphics.DrawPolygon%2A> Yöntemi otomatik olarak bir satırından çizerek Çokgen kapatır (30, 60) başlangıç noktası (0, 0) dön.  
  
 [!code-csharp[LinesCurvesAndShapes#111](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#111)]
 [!code-vb[LinesCurvesAndShapes#111](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#111)]  
  
 Aşağıdaki çizimde Çokgen gösterir.  
  
 ![Çokgen](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art08.gif "Aboutgdip02_art08")  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Nasıl yapılır: Kalem Oluşturma](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
