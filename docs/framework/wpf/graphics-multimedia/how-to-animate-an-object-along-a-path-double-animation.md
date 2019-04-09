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
ms.openlocfilehash: 54f345bbe6b513e3593cbf45ba190d4a44228424
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101451"
---
# <a name="how-to-animate-an-object-along-a-path-double-animation"></a><span data-ttu-id="70326-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Çift Animasyon)</span><span class="sxs-lookup"><span data-stu-id="70326-102">How to: Animate an Object Along a Path (Double Animation)</span></span>
<span data-ttu-id="70326-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> sınıfı tarafından tanımlanan yol bir nesneyi taşımak için bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="70326-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> class to move an object along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="70326-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="70326-104">Example</span></span>  
 <span data-ttu-id="70326-105">Aşağıdaki iki örnekte <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> bir dikdörtgen geometrik yol boyunca taşımak için nesneler:</span><span class="sxs-lookup"><span data-stu-id="70326-105">The following example uses two <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path:</span></span>  
  
-   <span data-ttu-id="70326-106">İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır <xref:System.Windows.Media.TranslateTransform.X%2A> , <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanır.</span><span class="sxs-lookup"><span data-stu-id="70326-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.X%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="70326-107">Yatay olarak yol boyunca taşımak dikdörtgeni kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="70326-107">It makes the rectangle move horizontally along the path.</span></span>  
  
-   <span data-ttu-id="70326-108">İkinci <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır <xref:System.Windows.Media.TranslateTransform.Y%2A> , <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanır.</span><span class="sxs-lookup"><span data-stu-id="70326-108">The second <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates the <xref:System.Windows.Media.TranslateTransform.Y%2A> of the <xref:System.Windows.Media.TranslateTransform> applied to the rectangle.</span></span> <span data-ttu-id="70326-109">Bu dikdörtgeni dikey yol boyunca taşır.</span><span class="sxs-lookup"><span data-stu-id="70326-109">It makes the rectangle move vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/doubleanimationusingpathexample.xaml#doubleanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/DoubleAnimationUsingPathExample.cs#doubleanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#DoubleAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/DoubleAnimationUsingPathExample.vb#doubleanimationusingpathwholepage)]  
  
 <span data-ttu-id="70326-110">Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="70326-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="70326-111">Geometrik yol kullanarak nesneyi taşımak, başka bir yolu bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesne.</span><span class="sxs-lookup"><span data-stu-id="70326-111">Another way to move an object using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object.</span></span> <span data-ttu-id="70326-112">Bir örnek için bkz. [bir nesne boyunca bir yolu (Matris Animasyonu) animasyon](how-to-animate-an-object-along-a-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="70326-112">For an example, see [Animate an Object Along a Path (Matrix Animation)](how-to-animate-an-object-along-a-path-matrix-animation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70326-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70326-113">See also</span></span>

- [<span data-ttu-id="70326-114">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="70326-114">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="70326-115">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="70326-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
