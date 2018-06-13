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
ms.openlocfilehash: 639e28d9b809d6fb5eed3a002bca1ffc40913896
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558787"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="cb2c1-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="cb2c1-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="cb2c1-103">Bu örnek, nasıl kullanılacağını gösterir. bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> hale getirmeyi nesnesine bir <xref:System.Windows.Point> boyunca eğik bir yolu.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb2c1-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="cb2c1-104">Example</span></span>  
 <span data-ttu-id="cb2c1-105">Aşağıdaki örnek taşır bir <xref:System.Windows.Media.EllipseGeometry> tarafından tanımlanan bir yol boyunca bir <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="cb2c1-106">Elips geometri 's <xref:System.Windows.Media.EllipseGeometry.Center%2A> geçen özelliği bir <xref:System.Windows.Point> değeri, animasyon olarak oluşturmak, elips geometri taşımak için onun konumunu belirler; kendi <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="cb2c1-107">Örnek kullanan bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> animasyon için <xref:System.Windows.Media.EllipseGeometry> nesnenin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="cb2c1-108">Tam bir örnek için bkz: [yol animasyonu örneği](http://go.microsoft.com/fwlink/?LinkID=160028).</span><span class="sxs-lookup"><span data-stu-id="cb2c1-108">For the complete sample, see [Path Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160028).</span></span>  
  
 <span data-ttu-id="cb2c1-109">Kullanılan Yukarıdaki örnek kod sürümü bir <xref:System.Windows.Media.Animation.Storyboard> animasyon için <xref:System.Windows.Media.EllipseGeometry>rağmen yalnızca bir animasyon uygulandı.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="cb2c1-110">A <xref:System.Windows.Media.Animation.Storyboard> genellikle animasyonlarına aynı tarafından denetlenmesi için birden çok animasyon uygulamak için en kolay yoludur <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="cb2c1-111">Ancak, tek bir animasyonu kod kullanırken bir özelliğe uygulamak için daha kolay bir yolu kullanmaktır <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="cb2c1-112">Bir örnek için bkz: [özelliği olmadan kullanarak bir film şeridi animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="cb2c1-112">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb2c1-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="cb2c1-113">See Also</span></span>  
 [<span data-ttu-id="cb2c1-114">Yol animasyonu örneği</span><span class="sxs-lookup"><span data-stu-id="cb2c1-114">Path Animation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160028)  
 [<span data-ttu-id="cb2c1-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="cb2c1-115">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="cb2c1-116">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="cb2c1-116">Path Animation How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)
