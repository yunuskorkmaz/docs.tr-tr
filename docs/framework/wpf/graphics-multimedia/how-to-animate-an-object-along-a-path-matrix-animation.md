---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (matrix animation)
- matrix animation [WPF]
ms.assetid: 7000e697-1414-468c-b915-cf66062fc49e
ms.openlocfilehash: 7dfc233fe60e1cea293edc44a2bba79dc6962f7c
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452915"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="b0c4a-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="b0c4a-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="b0c4a-103">Bu örnek, bir <xref:System.Windows.Media.PathGeometry>tarafından tanımlanan yol üzerinde bir nesneye animasyon uygulamak için <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sınıfını nasıl kullanacağınızı gösterir.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0c4a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b0c4a-104">Example</span></span>  
 <span data-ttu-id="b0c4a-105">Aşağıdaki örnek, aşağıdakileri yaparak bir nesneyi yol üzerinde hareketlendirir:</span><span class="sxs-lookup"><span data-stu-id="b0c4a-105">The following example animates an object along a path by doing the following:</span></span>  
  
- <span data-ttu-id="b0c4a-106">Taşımak için nesnesine bir <xref:System.Windows.Media.MatrixTransform> uygular.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
- <span data-ttu-id="b0c4a-107"><xref:System.Windows.Media.PathGeometry>kullanarak yolu tanımlar.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
- <span data-ttu-id="b0c4a-108">Bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> oluşturur ve <xref:System.Windows.Media.MatrixTransform><xref:System.Windows.Media.Matrix> özelliğine animasyon uygulamak için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="b0c4a-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> <xref:System.Windows.Media.PathGeometry> alır ve <xref:System.Windows.Media.Matrix> değerler oluşturmak için onu kullanır.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="b0c4a-110">Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="b0c4a-110">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span> <span data-ttu-id="b0c4a-111">Geometrik yollar hakkında daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b0c4a-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0c4a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0c4a-112">See also</span></span>

- [<span data-ttu-id="b0c4a-113">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="b0c4a-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="b0c4a-114">Yol animasyon örneği</span><span class="sxs-lookup"><span data-stu-id="b0c4a-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="b0c4a-115">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="b0c4a-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
