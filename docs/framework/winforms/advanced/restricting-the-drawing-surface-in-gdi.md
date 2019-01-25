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
ms.openlocfilehash: 3784c833098a5585c5cdc38014d5a9542daf39f2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54583417"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>GDI+'da Çizim Yüzeyini Sınırlandırma
Belirli bir dikdörtgen veya bölgeye çizim kısıtlama kırpma içerir. Aşağıdaki çizim dize "Hello" Kalp şeklindeki bir bölgeye kırpılarak olarak gösterir.  
  
 ![Kısıtlanmış çizim yüzeyi](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Bölgeler ile kırpma  
 Yolları bölgelerde oluşturulabilir ve kırpma için anahatları belirlenmiş metin kullanabilmeniz için yolları anahatlarını dizeleri içerebilir. Aşağıdaki çizimde, bir dizi için bir metin dizesinin iç kırpılarak Eşmerkezli üç nokta simgesini gösterir.  
  
 ![Kısıtlanmış çizim yüzeyi](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Kırpma ile çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesne, ayarlayın, <xref:System.Drawing.Graphics.Clip%2A> özelliği ve ardından, çizim yöntemleri aynı çağrı <xref:System.Drawing.Graphics> nesnesi:  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)
- [Bölgeleri Kullanma](../../../../docs/framework/winforms/advanced/using-regions.md)
