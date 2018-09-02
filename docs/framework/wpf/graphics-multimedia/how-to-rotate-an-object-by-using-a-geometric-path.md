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
ms.openlocfilehash: 6d6d21f3f7b609cb2933093a6990425deb39d4a6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43398154"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="65575-102">Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="65575-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="65575-103">Bu örnek nasıl döndürüleceğini (pivot) bir nesnenin tarafından tanımlanan bir geometrik yol gösterir. bir <xref:System.Windows.Media.PathGeometry> nesne.</span><span class="sxs-lookup"><span data-stu-id="65575-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65575-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="65575-104">Example</span></span>  
 <span data-ttu-id="65575-105">Aşağıdaki örnek, üç kullanır <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> bir dikdörtgen geometrik yol nesneleri.</span><span class="sxs-lookup"><span data-stu-id="65575-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
-   <span data-ttu-id="65575-106">İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır bir <xref:System.Windows.Media.RotateTransform> dikdörtgene uygulanır.</span><span class="sxs-lookup"><span data-stu-id="65575-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="65575-107">Animasyonun açı değerlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="65575-107">The animation generates angle values.</span></span> <span data-ttu-id="65575-108">Bu dikdörtgeni (Özet) yolun dağılımlarını döndür.</span><span class="sxs-lookup"><span data-stu-id="65575-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
-   <span data-ttu-id="65575-109">Diğer iki nesnelere animasyon <xref:System.Windows.Media.TranslateTransform.X%2A> ve <xref:System.Windows.Media.TranslateTransform.Y%2A> değerlerini bir <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanır.</span><span class="sxs-lookup"><span data-stu-id="65575-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="65575-110">Bunlar, yatay ve dikey olarak yol boyunca taşımak dikdörtgeni.</span><span class="sxs-lookup"><span data-stu-id="65575-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="65575-111">Geometrik yol kullanarak nesneyi döndürme için başka bir yolu bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesne ve ayarlayın, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="65575-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="65575-112">Daha fazla bilgi ve örnek için bkz. [(Matris Animasyonu) geometrik yol kullanarak nesneyi döndürme](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="65575-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](../../../../docs/framework/wpf/graphics-multimedia/how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="65575-113">Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="65575-113">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65575-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65575-114">See Also</span></span>  
 [<span data-ttu-id="65575-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="65575-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="65575-116">Yol animasyonu örneği</span><span class="sxs-lookup"><span data-stu-id="65575-116">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="65575-117">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="65575-117">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
