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
# <a name="restricting-the-drawing-surface-in-gdi"></a><span data-ttu-id="f3065-102">GDI+'da Çizim Yüzeyini Sınırlandırma</span><span class="sxs-lookup"><span data-stu-id="f3065-102">Restricting the Drawing Surface in GDI+</span></span>
<span data-ttu-id="f3065-103">Belirli bir dikdörtgen veya bölgeye çizim kısıtlama kırpma içerir.</span><span class="sxs-lookup"><span data-stu-id="f3065-103">Clipping involves restricting drawing to a certain rectangle or region.</span></span> <span data-ttu-id="f3065-104">Aşağıdaki çizimde dizesi "Merhaba" Kalp şeklindeki bir bölgeye kırpılmış olarak gösterir.</span><span class="sxs-lookup"><span data-stu-id="f3065-104">The following illustration shows the string "Hello" clipped to a heart-shaped region.</span></span>  
  
 <span data-ttu-id="f3065-105">![Kısıtlanmış çizim yüzeyi](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span><span class="sxs-lookup"><span data-stu-id="f3065-105">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art30.gif "AboutGdip02_Art30")</span></span>  
  
## <a name="clipping-with-regions"></a><span data-ttu-id="f3065-106">Bölgeleri ile kırpma</span><span class="sxs-lookup"><span data-stu-id="f3065-106">Clipping with Regions</span></span>  
 <span data-ttu-id="f3065-107">Bölgeler yolları oluşturulabilir ve kırpma için anahatları belirlenmiş metin kullanabilmeniz için yollar dizeleri anahatları içerebilir.</span><span class="sxs-lookup"><span data-stu-id="f3065-107">Regions can be constructed from paths, and paths can contain the outlines of strings, so you can use outlined text for clipping.</span></span> <span data-ttu-id="f3065-108">Aşağıdaki resimde bir metin dizesinin iç için kırpılmış Eşmerkezli üç nokta kümesi gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f3065-108">The following illustration shows a set of concentric ellipses clipped to the interior of a string of text.</span></span>  
  
 <span data-ttu-id="f3065-109">![Kısıtlanmış çizim yüzeyi](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span><span class="sxs-lookup"><span data-stu-id="f3065-109">![Restricted Drawing Surface](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art31.gif "AboutGdip02_Art31")</span></span>  
  
 <span data-ttu-id="f3065-110">Kırpma ile çizmek için oluşturma bir <xref:System.Drawing.Graphics> nesne, ayarlayın, <xref:System.Drawing.Graphics.Clip%2A> özelliği ve ardından, çizim yöntemleri aynı çağrı <xref:System.Drawing.Graphics> nesnesi:</span><span class="sxs-lookup"><span data-stu-id="f3065-110">To draw with clipping, create a <xref:System.Drawing.Graphics> object, set its <xref:System.Drawing.Graphics.Clip%2A> property, and then call the drawing methods of that same <xref:System.Drawing.Graphics> object:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#91](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#91)]
 [!code-vb[LinesCurvesAndShapes#91](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#91)]  
  
## <a name="see-also"></a><span data-ttu-id="f3065-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3065-111">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Region?displayProperty=nameWithType>  
 [<span data-ttu-id="f3065-112">Çizgiler, Eğriler ve Şekiller</span><span class="sxs-lookup"><span data-stu-id="f3065-112">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="f3065-113">Bölgeleri Kullanma</span><span class="sxs-lookup"><span data-stu-id="f3065-113">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)
