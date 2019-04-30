---
title: 'Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], objects along paths (point animation)
- point animation [WPF]
ms.assetid: 1fa3f817-35bc-41a1-b366-f5a20b70da0c
ms.openlocfilehash: 4ef28118975d02500916676ca50e0f9622c7a3e2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651460"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="eb42e-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="eb42e-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="eb42e-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animasyon uygulamak için nesne bir <xref:System.Windows.Point> eğri yol.</span><span class="sxs-lookup"><span data-stu-id="eb42e-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb42e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="eb42e-104">Example</span></span>  
 <span data-ttu-id="eb42e-105">Aşağıdaki örnek taşır bir <xref:System.Windows.Media.EllipseGeometry> tarafından tanımlanan yol bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="eb42e-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="eb42e-106">Elips geometrisinin <xref:System.Windows.Media.EllipseGeometry.Center%2A> alan, özelliği bir <xref:System.Windows.Point> animasyon olarak oluşturmak, elips geometrisini taşımak için; konumunu belirtir, değeri kendi <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="eb42e-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="eb42e-107">Örnekte bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry> nesnenin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="eb42e-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="eb42e-108">Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="eb42e-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="eb42e-109">Önceki örnekte kullanılan kod sürümünü bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry>, yalnızca bir animasyon uygulanmış olmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="eb42e-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="eb42e-110">A <xref:System.Windows.Media.Animation.Storyboard> genellikle animasyonlarına aynı tarafından denetlenebilir olduğundan, birden çok animasyon uygulamak için en kolay yoludur <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="eb42e-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="eb42e-111">Ancak, tek bir animasyonu kod kullanarak bir özelliğe uygulamak için daha kolay bir yolu kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="eb42e-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="eb42e-112">Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="eb42e-112">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb42e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="eb42e-113">See also</span></span>

- [<span data-ttu-id="eb42e-114">Yol animasyonu örneği</span><span class="sxs-lookup"><span data-stu-id="eb42e-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)
- [<span data-ttu-id="eb42e-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="eb42e-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="eb42e-116">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="eb42e-116">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
