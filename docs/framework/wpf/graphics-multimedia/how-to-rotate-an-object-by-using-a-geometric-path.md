---
title: 'Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
ms.assetid: cb31ca4d-f05a-4c6b-9a18-4b6faaf38d45
ms.openlocfilehash: a351fdc936f634b7c57ba5a49e51501f7572a3c9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186869"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="2c53d-102">Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="2c53d-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="2c53d-103">Bu örnek, bir <xref:System.Windows.Media.PathGeometry> nesne tarafından tanımlanan geometrik bir yol boyunca bir nesneyi nasıl döndürecek (döndürmeyi) gösterir.</span><span class="sxs-lookup"><span data-stu-id="2c53d-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c53d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="2c53d-104">Example</span></span>  
 <span data-ttu-id="2c53d-105">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> geometrik bir yol boyunca bir dikdörtgeni taşımak için üç nesne kullanır.</span><span class="sxs-lookup"><span data-stu-id="2c53d-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
- <span data-ttu-id="2c53d-106"><xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> İlk animasyon dikdörtgen <xref:System.Windows.Media.RotateTransform> uygulanır.</span><span class="sxs-lookup"><span data-stu-id="2c53d-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="2c53d-107">Animasyon açı değerleri oluşturur.</span><span class="sxs-lookup"><span data-stu-id="2c53d-107">The animation generates angle values.</span></span> <span data-ttu-id="2c53d-108">Dikdörtgenin yolun hatları boyunca dönmesini (pivot) sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c53d-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
- <span data-ttu-id="2c53d-109">Diğer iki nesne, dikdörtgeniçin <xref:System.Windows.Media.TranslateTransform.X%2A> <xref:System.Windows.Media.TranslateTransform.Y%2A> uygulanan bir <xref:System.Windows.Media.TranslateTransform> nesnenin değerlerini ve değerlerini animasyona salar.</span><span class="sxs-lookup"><span data-stu-id="2c53d-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="2c53d-110">Dikdörtgenin yol boyunca yatay ve dikey olarak hareket ettirin.</span><span class="sxs-lookup"><span data-stu-id="2c53d-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="2c53d-111">Geometrik bir yol kullanarak bir nesneyi döndürmenin <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> başka bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> yolu `true`da nesneyi kullanmak ve özelliğini .'e ayarlamaktır.</span><span class="sxs-lookup"><span data-stu-id="2c53d-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="2c53d-112">Daha fazla bilgi ve örnek için [bkz.](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md)</span><span class="sxs-lookup"><span data-stu-id="2c53d-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="2c53d-113">Tam örnek için [Yol Animasyon Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)bakın.</span><span class="sxs-lookup"><span data-stu-id="2c53d-113">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c53d-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c53d-114">See also</span></span>

- [<span data-ttu-id="2c53d-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="2c53d-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="2c53d-116">Yol Animasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="2c53d-116">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="2c53d-117">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="2c53d-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
