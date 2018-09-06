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
ms.openlocfilehash: d6dc79cd7a15aef2a4168fffb293c5e1f33cde08
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870360"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="a1357-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="a1357-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="a1357-103">Bu örnek nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animasyon uygulamak için nesne bir <xref:System.Windows.Point> eğri yol.</span><span class="sxs-lookup"><span data-stu-id="a1357-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1357-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="a1357-104">Example</span></span>  
 <span data-ttu-id="a1357-105">Aşağıdaki örnek taşır bir <xref:System.Windows.Media.EllipseGeometry> tarafından tanımlanan yol bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="a1357-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a1357-106">Elips geometrisinin <xref:System.Windows.Media.EllipseGeometry.Center%2A> alan, özelliği bir <xref:System.Windows.Point> animasyon olarak oluşturmak, elips geometrisini taşımak için; konumunu belirtir, değeri kendi <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1357-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="a1357-107">Örnekte bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry> nesnenin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="a1357-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="a1357-108">Tam bir örnek için bkz. [yol animasyonu örneği](https://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="a1357-108">For the complete sample, see [Path Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="a1357-109">Önceki örnekte kullanılan kod sürümünü bir <xref:System.Windows.Media.Animation.Storyboard> animasyon uygulamak için <xref:System.Windows.Media.EllipseGeometry>, yalnızca bir animasyon uygulanmış olmasına rağmen.</span><span class="sxs-lookup"><span data-stu-id="a1357-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="a1357-110">A <xref:System.Windows.Media.Animation.Storyboard> genellikle animasyonlarına aynı tarafından denetlenebilir olduğundan, birden çok animasyon uygulamak için en kolay yoludur <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="a1357-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="a1357-111">Ancak, tek bir animasyonu kod kullanarak bir özelliğe uygulamak için daha kolay bir yolu kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="a1357-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="a1357-112">Bir örnek için bkz. [özelliği olmadan kullanarak bir görsel taslak animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="a1357-112">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1357-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a1357-113">See Also</span></span>  
 [<span data-ttu-id="a1357-114">Yol animasyonu örneği</span><span class="sxs-lookup"><span data-stu-id="a1357-114">Path Animation Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="a1357-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="a1357-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a1357-116">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="a1357-116">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
