---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (double animation)
- double animation [WPF]
ms.assetid: 5a3c4a99-f303-42ad-a52a-e4794bb1798e
ms.openlocfilehash: 084caac26fd68b6914ec3858652ec44557a0dbd7
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452863"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="ddae0-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)</span><span class="sxs-lookup"><span data-stu-id="ddae0-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="ddae0-103">Bu örnek, bir nesneyi bir <xref:System.Windows.Media.PathGeometry>tarafından tanımlanan yol üzerinde taşımak için <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ddae0-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ddae0-104">Example</span></span>  
 <span data-ttu-id="ddae0-105">Aşağıdaki örnek, bir dikdörtgeni geometrik yol üzerinde taşımak için iki <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> nesnesi kullanır:</span><span class="sxs-lookup"><span data-stu-id="ddae0-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
- <span data-ttu-id="ddae0-106">İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>, dikdörtgene uygulanan <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.X%2A> hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="ddae0-107">Dikdörtgeni yol üzerinde yatay olarak hareket ettirin.</span><span class="sxs-lookup"><span data-stu-id="ddae0-107">It makes the rectangle move horizontally along the path.</span></span>  
  
- <span data-ttu-id="ddae0-108">İkinci <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>, dikdörtgene uygulanan <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.TranslateTransform.Y%2A> hareketlendirir.</span><span class="sxs-lookup"><span data-stu-id="ddae0-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="ddae0-109">Dikdörtgeni yol üzerinde dikey olarak hareket ettirin.</span><span class="sxs-lookup"><span data-stu-id="ddae0-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="ddae0-110">Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="ddae0-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="ddae0-111">Bir geometrik yol kullanarak nesneyi taşımanın bir başka yolu da <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesnesi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="ddae0-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="ddae0-112">Bir örnek için bkz. bir [nesnenin yol üzerinde animasyonunu oluşturma (matris animasyonu)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="ddae0-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddae0-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ddae0-113">See also</span></span>

- [<span data-ttu-id="ddae0-114">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="ddae0-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ddae0-115">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ddae0-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
