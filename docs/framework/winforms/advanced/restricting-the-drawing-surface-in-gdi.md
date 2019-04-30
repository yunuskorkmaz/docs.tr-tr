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
ms.openlocfilehash: d0508166f905b45789ce638b03d0747dd6fa904e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61672646"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a>GDI+'da Çizim Yüzeyini Sınırlandırma
Belirli bir dikdörtgen veya bölgeye çizim kısıtlama kırpma içerir. Aşağıdaki çizim dize "Hello" Kalp şeklindeki bir bölgeye kırpılarak olarak gösterir.  
  
 ![Kısıtlanmış çizim yüzeyi](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")  
  
## <a name="clipping-with-regions"></a>Bölgeler ile kırpma  
 Yolları bölgelerde oluşturulabilir ve kırpma için anahatları belirlenmiş metin kullanabilmeniz için yolları anahatlarını dizeleri içerebilir. Aşağıdaki çizimde, bir dizi için bir metin dizesinin iç kırpılarak Eşmerkezli üç nokta simgesini gösterir.  
  
 ![Kısıtlanmış çizim yüzeyi](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")  
  
 Kırpma ile çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesne, ayarlayın, <xref:System.Drawing.Graphics.Clip%2A> özelliği ve ardından, çizim yöntemleri aynı çağrı <xref:System.Drawing.Graphics> nesnesi:  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [Çizgiler, Eğriler ve Şekiller](lines-curves-and-shapes.md)
- [Bölgeleri Kullanma](using-regions.md)
