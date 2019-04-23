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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59074969"
---
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="2bfb4-102">GDI+'da Çizim Yüzeyini Sınırlandırma</span><span class="sxs-lookup"><span data-stu-id="2bfb4-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="2bfb4-103">Belirli bir dikdörtgen veya bölgeye çizim kısıtlama kırpma içerir.</span><span class="sxs-lookup"><span data-stu-id="2bfb4-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="2bfb4-104">Aşağıdaki çizim dize "Hello" Kalp şeklindeki bir bölgeye kırpılarak olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="2bfb4-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="2bfb4-105">![Kısıtlanmış çizim yüzeyi](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="2bfb4-105">![Restricted Drawing Surface](./media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="2bfb4-106">Bölgeler ile kırpma</span><span class="sxs-lookup"><span data-stu-id="2bfb4-106">Clipping with Regions</span></span>  
 <span data-ttu-id="2bfb4-107">Yolları bölgelerde oluşturulabilir ve kırpma için anahatları belirlenmiş metin kullanabilmeniz için yolları anahatlarını dizeleri içerebilir.</span><span class="sxs-lookup"><span data-stu-id="2bfb4-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="2bfb4-108">Aşağıdaki çizimde, bir dizi için bir metin dizesinin iç kırpılarak Eşmerkezli üç nokta simgesini gösterir.</span><span class="sxs-lookup"><span data-stu-id="2bfb4-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="2bfb4-109">![Kısıtlanmış çizim yüzeyi](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="2bfb4-109">![Restricted Drawing Surface](./media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="2bfb4-110">Kırpma ile çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesne, ayarlayın, <xref:System.Drawing.Graphics.Clip%2A> özelliği ve ardından, çizim yöntemleri aynı çağrı <xref:System.Drawing.Graphics> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="2bfb4-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="2bfb4-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2bfb4-111">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Region?displayProperty=nameWithType>
- [<span data-ttu-id="2bfb4-112">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="2bfb4-112">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="2bfb4-113">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="2bfb4-113">Using Regions</span></span>](using-regions.md)
