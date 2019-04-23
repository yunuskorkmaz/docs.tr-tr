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
ms.openlocfilehash: ab15126680b7d8c6936246a7dae2f67c7541233b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190931"
---
# <a name="how-to-animate-an-object-along-a-path-matrix-animation"></a><span data-ttu-id="0bab1-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (Matris Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="0bab1-102">How to: Animate an Object Along a Path (Matrix Animation)</span></span>
<span data-ttu-id="0bab1-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> sınıfının bir nesnenin tarafından tanımlanan bir yol üzerinde animasyonunu bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0bab1-103">This example shows how to use the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> class to animate an object along a path that is defined by a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bab1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="0bab1-104">Example</span></span>  
 <span data-ttu-id="0bab1-105">Aşağıdaki örnek, aşağıdakileri yaparak bir nesnenin yol canlandırın:</span><span class="sxs-lookup"><span data-stu-id="0bab1-105">The following example animates an object along a path by doing the following:</span></span>  
  
-   <span data-ttu-id="0bab1-106">Geçerli bir <xref:System.Windows.Media.MatrixTransform> taşımak için nesne.</span><span class="sxs-lookup"><span data-stu-id="0bab1-106">Applies a <xref:System.Windows.Media.MatrixTransform> to the object in order to move it.</span></span>  
  
-   <span data-ttu-id="0bab1-107">Yolu kullanarak tanımlayan bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="0bab1-107">Defines the path by using a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
-   <span data-ttu-id="0bab1-108">Oluşturur bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> ve animasyon uygulamak için kullandığı <xref:System.Windows.Media.Matrix> özelliği <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="0bab1-108">Creates a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and uses it to animate the <xref:System.Windows.Media.Matrix> property of the <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="0bab1-109"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> Alır <xref:System.Windows.Media.PathGeometry> ve oluşturmak için kullandığı <xref:System.Windows.Media.Matrix> değerleri.</span><span class="sxs-lookup"><span data-stu-id="0bab1-109">The <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> takes the <xref:System.Windows.Media.PathGeometry> and uses it to generate <xref:System.Windows.Media.Matrix> values.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathexample.xaml#matrixanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathExample.cs#matrixanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathExample.vb#matrixanimationusingpathwholepage)]  
  
 <span data-ttu-id="0bab1-110">Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="0bab1-110">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span> <span data-ttu-id="0bab1-111">Geometrik yollar hakkında daha fazla bilgi için bkz. [geometrisi](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="0bab1-111">For more information about geometric paths, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bab1-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0bab1-112">See also</span></span>

- [<span data-ttu-id="0bab1-113">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="0bab1-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="0bab1-114">Yol animasyonu örneği</span><span class="sxs-lookup"><span data-stu-id="0bab1-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
- [<span data-ttu-id="0bab1-115">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="0bab1-115">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
