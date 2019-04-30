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
ms.openlocfilehash: 3e35169da7297ec62e0114ab21f4ba81c0a656ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651252"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path"></a><span data-ttu-id="1c1f4-102">Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme</span><span class="sxs-lookup"><span data-stu-id="1c1f4-102">How to: Rotate an Object by Using a Geometric Path</span></span>
<span data-ttu-id="1c1f4-103">Bu örnek nasıl döndürüleceğini (pivot) bir nesnenin tarafından tanımlanan bir geometrik yol gösterir. bir <xref:System.Windows.Media.PathGeometry> nesne.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-103">This example shows how to rotate (pivot) an object along a geometric path that is defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c1f4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1c1f4-104">Example</span></span>  
 <span data-ttu-id="1c1f4-105">Aşağıdaki örnek, üç kullanır <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> bir dikdörtgen geometrik yol nesneleri.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-105">The following example uses three <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> objects to move a rectangle along a geometric path.</span></span>  
  
- <span data-ttu-id="1c1f4-106">İlk <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> canlandırır bir <xref:System.Windows.Media.RotateTransform> dikdörtgene uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-106">The first <xref:System.Windows.Media.Animation.DoubleAnimationUsingPath> animates a <xref:System.Windows.Media.RotateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="1c1f4-107">Animasyonun açı değerlerini oluşturur.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-107">The animation generates angle values.</span></span> <span data-ttu-id="1c1f4-108">Bu dikdörtgeni (Özet) yolun dağılımlarını döndür.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-108">It makes the rectangle rotate (pivot) along the contours of the path.</span></span>  
  
- <span data-ttu-id="1c1f4-109">Diğer iki nesnelere animasyon <xref:System.Windows.Media.TranslateTransform.X%2A> ve <xref:System.Windows.Media.TranslateTransform.Y%2A> değerlerini bir <xref:System.Windows.Media.TranslateTransform> dikdörtgene uygulanır.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-109">The other two objects animate the <xref:System.Windows.Media.TranslateTransform.X%2A> and <xref:System.Windows.Media.TranslateTransform.Y%2A> values of a <xref:System.Windows.Media.TranslateTransform> that is applied to the rectangle.</span></span> <span data-ttu-id="1c1f4-110">Bunlar, yatay ve dikey olarak yol boyunca taşımak dikdörtgeni.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-110">They make the rectangle move horizontally and vertically along the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/rotateanimationusingpathexample.xaml#rotateanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/RotateAnimationUsingPathExample.cs#rotateanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#RotateAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/RotateAnimationUsingPathExample.vb#rotateanimationusingpathwholepage)]  
  
 <span data-ttu-id="1c1f4-111">Geometrik yol kullanarak nesneyi döndürme için başka bir yolu bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> nesne ve ayarlayın, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliğini `true`.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-111">Another way to rotate an object by using a geometric path is to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object and set its <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property to `true`.</span></span> <span data-ttu-id="1c1f4-112">Daha fazla bilgi ve örnek için bkz. [(Matris Animasyonu) geometrik yol kullanarak nesneyi döndürme](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span><span class="sxs-lookup"><span data-stu-id="1c1f4-112">For more information and an example, see [Rotate an Object by Using a Geometric Path (Matrix Animation)](how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation.md).</span></span>  
  
 <span data-ttu-id="1c1f4-113">Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="1c1f4-113">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c1f4-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1c1f4-114">See also</span></span>

- [<span data-ttu-id="1c1f4-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="1c1f4-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="1c1f4-116">Yol animasyonu örneği</span><span class="sxs-lookup"><span data-stu-id="1c1f4-116">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
- [<span data-ttu-id="1c1f4-117">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="1c1f4-117">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
