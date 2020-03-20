---
title: 'Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme (Matris Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometric paths [WPF], rotating objects by
- rotating objects by geometric paths [WPF]
- matrix animation [WPF]
ms.assetid: 877dc9aa-6bdc-4beb-8772-3efaec32c0f0
ms.openlocfilehash: 63dc873a2b840ea3f870a8c60c5691ab271c1c9f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187408"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="faa2e-102">Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme (Matris Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="faa2e-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="faa2e-103">Bu örnek, bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> <xref:System.Windows.Media.PathGeometry> nesne <xref:System.Windows.Media.MatrixTransform> tarafından tanımlanan geometrik bir yol boyunca bir nesneyi döndürmek (döndürmek) için a ve a'nın nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="faa2e-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="faa2e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="faa2e-104">Example</span></span>  
 <span data-ttu-id="faa2e-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> bir <xref:System.Windows.Media.MatrixTransform>. özelliğini <xref:System.Windows.Media.MatrixTransform.Matrix%2A> canlandırmak için nesneyi kullanır.</span><span class="sxs-lookup"><span data-stu-id="faa2e-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="faa2e-106">Bir <xref:System.Windows.Media.MatrixTransform> düğmeye uygulanır ve eğri bir yol boyunca hareket etmesini neden olur.</span><span class="sxs-lookup"><span data-stu-id="faa2e-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="faa2e-107"><xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> Özellik ayarlandığı için, `true`dikdörtgen yolun teğet boyunca döner.</span><span class="sxs-lookup"><span data-stu-id="faa2e-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="faa2e-108">Tam örnek için [Yol Animasyon Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)bakın.</span><span class="sxs-lookup"><span data-stu-id="faa2e-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="faa2e-109">Yalnızca bir animasyon uygulanmış olsa <xref:System.Windows.Media.Animation.Storyboard> <xref:System.Windows.Media.EllipseGeometry>bile, önceki örneğin kod sürümü , animasyon için a kullanılır.</span><span class="sxs-lookup"><span data-stu-id="faa2e-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="faa2e-110">Koddaki bir özelliğe tek bir animasyon uygulamanın <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> daha kolay bir yolu yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="faa2e-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="faa2e-111">Örneğin, Bir [Storyboard kullanmadan bir Özellik Animasyon](how-to-animate-a-property-without-using-a-storyboard.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="faa2e-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="faa2e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="faa2e-112">See also</span></span>

- [<span data-ttu-id="faa2e-113">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="faa2e-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="faa2e-114">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="faa2e-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="faa2e-115">Yol Animasyon Örneği</span><span class="sxs-lookup"><span data-stu-id="faa2e-115">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
