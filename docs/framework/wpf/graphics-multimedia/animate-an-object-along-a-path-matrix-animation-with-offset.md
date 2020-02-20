---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- offset accumulation [WPF]
- animation [WPF], objects along paths (matrix animation with offset accumulation)
- matrix animation with offset accumulation [WPF]
ms.assetid: 1bca90ef-9832-4128-8ed6-62908e7ec146
ms.openlocfilehash: 8b3975ef5031b50381dfa9baf7f34a58fc05ab4e
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77453110"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="d63cd-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="d63cd-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="d63cd-103">Bu örnek, bir nesnenin yol üzerinde animasyonunu yapmak için <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sınıfının nasıl kullanılacağını gösterir ve animasyonun, yineleme değerlerini tekrarlandığı şekilde birikmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="d63cd-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d63cd-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="d63cd-104">Example</span></span>  
 <span data-ttu-id="d63cd-105">Aşağıdaki örnek, bir düğmeye uygulanan bir <xref:System.Windows.Media.MatrixTransform> <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliğine animasyon eklemek için <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesnesini kullanır.</span><span class="sxs-lookup"><span data-stu-id="d63cd-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="d63cd-106">Sonuç olarak, bir düğme eğri yol üzerinde taşınıyor.</span><span class="sxs-lookup"><span data-stu-id="d63cd-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="d63cd-107">Buna ek olarak, örnek <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliğini `true`olarak ayarlar, bu da animasyon yinelendikçe animasyonlu matrisin sapmasını birikmesine neden olur.</span><span class="sxs-lookup"><span data-stu-id="d63cd-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="d63cd-108">Fark biriktiğinden, düğme, animasyon yinelendiğinde, başlangıç konumuna sıfırlamak yerine, ekran üzerinde daha fazla gider.</span><span class="sxs-lookup"><span data-stu-id="d63cd-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="d63cd-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliği, fark değerlerinin tekrarları üzerinden birikmesine neden olmasına rağmen, döndürme değerlerinin birikmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="d63cd-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="d63cd-110">Döndürme değerlerinin birikmesini sağlamak için, animasyonun <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> ve <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> özelliklerini `true`olarak ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="d63cd-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="d63cd-111">Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="d63cd-111">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="d63cd-112">Bir <xref:System.Windows.Media.Matrix> değerinin, fark birikmesi olmadan yol boyunca nasıl hareketlendirileceğini gösteren bir örnek için, bkz. bir [nesneye animasyon ekleme (matris animasyonu)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="d63cd-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d63cd-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d63cd-113">See also</span></span>

- [<span data-ttu-id="d63cd-114">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="d63cd-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="d63cd-115">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="d63cd-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
