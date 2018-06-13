---
title: GDI+'da Çizim Yüzeyini Sınırlandırma
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, clipping
- clipping [Windows Forms], using GDI+
- GDI+, restricting drawing surface
ms.assetid: 8b5f71d9-d2f0-4540-9c41-740f90fd4c26
ms.openlocfilehash: b457e94acb334dc012f017090c63189de372592d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523929"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>GDI+'da Çizim Yüzeyini Sınırlandırma
Belirli bir dikdörtgen veya bölgeye çizim kısıtlama kırpma içerir. Aşağıdaki çizimde dizesi "Merhaba" Kalp şeklindeki bir bölgeye kırpılmış olarak gösterir.  
  
 ![Kısıtlanmış çizim yüzeyi](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Bölgeleri ile kırpma  
 Bölgeler yolları oluşturulabilir ve kırpma için anahatları belirlenmiş metin kullanabilmeniz için yollar dizeleri anahatları içerebilir. Aşağıdaki resimde bir metin dizesinin iç için kırpılmış Eşmerkezli üç nokta kümesi gösterilmektedir.  
  
 ![Kısıtlanmış çizim yüzeyi](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Kırpma ile çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesne, ayarlayın, <xref:System.Drawing.Graphics.Clip%2A> özelliği ve ardından, çizim yöntemleri aynı çağrı <xref:System.Drawing.Graphics> nesnesi:  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [Bölgeleri Kullanma](../../../../docs/framework/winforms/advanced/using-regions.md)
