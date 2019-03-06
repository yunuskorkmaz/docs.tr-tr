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
ms.openlocfilehash: 57402ba24e8dc75f3563e71329b54db9cb96aaab
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369090"
---
# <a name="how-to-rotate-an-object-by-using-a-geometric-path-matrix-animation"></a><span data-ttu-id="5c573-102">Nasıl yapılır: Geometrik Yol Kullanarak Nesneyi Döndürme (Matris Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="5c573-102">How to: Rotate an Object by Using a Geometric Path (Matrix Animation)</span></span>
<span data-ttu-id="5c573-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> ve <xref:System.Windows.Media.MatrixTransform> (Özet) tarafından tanımlanan bir geometrik yol boyunca bir nesneyi döndürmek için bir <xref:System.Windows.Media.PathGeometry> nesne.</span><span class="sxs-lookup"><span data-stu-id="5c573-103">This example shows how to use a <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> and a <xref:System.Windows.Media.MatrixTransform> to rotate (pivot) an object along a geometric path defined by a <xref:System.Windows.Media.PathGeometry> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c573-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5c573-104">Example</span></span>  
 <span data-ttu-id="5c573-105">Aşağıdaki örnekte <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> animasyon uygulamak için nesne <xref:System.Windows.Media.MatrixTransform.Matrix%2A> özelliği bir <xref:System.Windows.Media.MatrixTransform>.</span><span class="sxs-lookup"><span data-stu-id="5c573-105">The following example uses the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath> object to animate the <xref:System.Windows.Media.MatrixTransform.Matrix%2A> property of a <xref:System.Windows.Media.MatrixTransform>.</span></span> <span data-ttu-id="5c573-106"><xref:System.Windows.Media.MatrixTransform> Düğmeye uygulanır ve eğik bir yolu boyunca taşımak neden olur.</span><span class="sxs-lookup"><span data-stu-id="5c573-106">The <xref:System.Windows.Media.MatrixTransform> is applied to a button and causes it to move along a curved path.</span></span> <span data-ttu-id="5c573-107">Çünkü <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> özelliği `true`, dikdörtgen yol tanjantını döndürür.</span><span class="sxs-lookup"><span data-stu-id="5c573-107">Because the <xref:System.Windows.Media.Animation.MatrixAnimationUsingPath.DoesRotateWithTangent%2A> property is set to `true`, the rectangle rotates along the tangent of the path.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/matrixanimationusingpathdoesrotatewithtangentexample.xaml#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/MatrixAnimationUsingPathDoesRotateWithTangentExample.cs#matrixanimationusingpathdoesrotatewithtangentwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#MatrixAnimationUsingPathDoesRotateWithTangentWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/MatrixAnimationUsingPathDoesRotateWithTangentExample.vb#matrixanimationusingpathdoesrotatewithtangentwholepage)]  
  
 <span data-ttu-id="5c573-108">Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="5c573-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="5c573-109">Önceki örnekte kullanılan kod sürümünü bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry>, yalnızca bir animasyon uygulanmış olmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="5c573-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="5c573-110">Kod bir özelliği tek bir animasyon uygulamak için daha kolay bir yolu kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="5c573-110">An easier way to apply a single animation to a property in code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="5c573-111">Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="5c573-111">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c573-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5c573-112">See also</span></span>
- [<span data-ttu-id="5c573-113">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="5c573-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="5c573-114">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5c573-114">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
- [<span data-ttu-id="5c573-115">Yol animasyonu örneği</span><span class="sxs-lookup"><span data-stu-id="5c573-115">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
