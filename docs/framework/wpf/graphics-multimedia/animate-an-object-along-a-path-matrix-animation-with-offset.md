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
ms.openlocfilehash: 77daf4efb913f2bc2606247178b6a6c4add29bd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33556815"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation-with-offset-accumulation"></a><span data-ttu-id="54801-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Sapma Birikmesi ile Matris Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="54801-102">How to: Animate an Object Along a Path (Matrix Animation with Offset Accumulation)</span></span>
<span data-ttu-id="54801-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sapması birikmesini animasyonun bir yol boyunca bir nesneyi hale getirmeyi ve sınıf değerleri yinelenecek şekilde.</span><span class="sxs-lookup"><span data-stu-id="54801-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path and have that animation accumulate its offset values as it repeats.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54801-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="54801-104">Example</span></span>  
 <span data-ttu-id="54801-105">Aşağıdaki örnek kullanır <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> hale getirmeyi nesnesine <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform> bir düğmeye uygulanan.</span><span class="sxs-lookup"><span data-stu-id="54801-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform> applied to a button.</span></span> <span data-ttu-id="54801-106">Sonuç olarak, bir düğme eğri bir yol boyunca taşır.</span><span class="sxs-lookup"><span data-stu-id="54801-106">As a result, a button moves along a curved path.</span></span>  
  
 <span data-ttu-id="54801-107">Ayrıca, örnek ayarlar <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliğine `true`, animasyon yinelendikçe animasyonlu matris uzaklığını neden olur.</span><span class="sxs-lookup"><span data-stu-id="54801-107">In addition, the example sets the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property to `true`, which causes the offset of the animated matrix to accumulate as the animation repeats.</span></span> <span data-ttu-id="54801-108">Uzaklık öğelerden çünkü düğme uzağa başlangıç konumunu sıfırlamak yerine animasyonu yineler ekrana arasında taşır.</span><span class="sxs-lookup"><span data-stu-id="54801-108">Because the offset accumulates, the button moves farther across the screen when the animation repeats, rather than resetting to the starting position.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexampleoffsetcumulative.xaml#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExampleOffsetCumulative.cs#matrixanimationusingpathoffsetcumulativewholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathOffsetCumulativeWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExampleOffsetCumulative.vb#matrixanimationusingpathoffsetcumulativewholepage)]  
  
 <span data-ttu-id="54801-109">Ancak Not <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> özelliği sapma değerlerinin tekrarları birikmesine neden olur, döndürme değerlerinin birikmesine neden olmaz.</span><span class="sxs-lookup"><span data-stu-id="54801-109">Note that, although the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsOffsetCumulative%2A> property causes offset values to accumulate over repetitions, it doesn't cause rotation values to accumulate.</span></span> <span data-ttu-id="54801-110">Animasyonun birikmesini döndürme değerlerini ayarlayın <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> ve <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> özelliklerine `true`.</span><span class="sxs-lookup"><span data-stu-id="54801-110">To make rotation values accumulate, set the animation's <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> and <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.IsAngleCumulative%2A> properties to `true`.</span></span>  
  
 <span data-ttu-id="54801-111">Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="54801-111">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="54801-112">Nasıl yapıldığını gösteren bir örnek bir <xref:System.Windows.Media.Matrix> değer uzaklık Birikme olmadan bir yol için bkz: [bir nesne boyunca bir yolu (Matris Animasyonu) animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="54801-112">For an example showing how to animate a <xref:System.Windows.Media.Matrix> value along a path without offset accumulation, see [Animate an Object Along a Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54801-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54801-113">See Also</span></span>  
 [<span data-ttu-id="54801-114">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="54801-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="54801-115">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="54801-115">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
