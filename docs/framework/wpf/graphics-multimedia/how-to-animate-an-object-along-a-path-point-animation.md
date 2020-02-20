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
ms.openlocfilehash: eff0c24a9369ffaa0cfca1cc46af4eff39f58a38
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452902"
---
# <a name="how-to-animate-an-object-along-a-path-point-animation"></a><span data-ttu-id="c0339-102">Nasıl yapılır: Bir Nesnenin Yol Üzerinde Animasyonunu Oluşturma (İşaret Etme Animasyonu)</span><span class="sxs-lookup"><span data-stu-id="c0339-102">How to: Animate an Object Along a Path (Point Animation)</span></span>
<span data-ttu-id="c0339-103">Bu örnek, bir <xref:System.Windows.Point> eğri yol üzerinde hareketlendirmek için bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> nesnesinin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="c0339-103">This example shows how to use a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> object to animate a <xref:System.Windows.Point> along a curved path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0339-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c0339-104">Example</span></span>  
 <span data-ttu-id="c0339-105">Aşağıdaki örnek, bir <xref:System.Windows.Media.EllipseGeometry> <xref:System.Windows.Media.PathGeometry>tarafından tanımlanan bir yol üzerinde taşıdır.</span><span class="sxs-lookup"><span data-stu-id="c0339-105">The following example moves an <xref:System.Windows.Media.EllipseGeometry> along a path defined by a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="c0339-106">Elips geometrisinin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği, bir <xref:System.Windows.Point> değeri alır, konumunu belirtir; elips geometrisini taşımak için <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliğine animasyon uygularsınız.</span><span class="sxs-lookup"><span data-stu-id="c0339-106">The ellipse geometry's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property, which takes a <xref:System.Windows.Point> value, specifies its position; to move the ellipse geometry, you animate its <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span> <span data-ttu-id="c0339-107">Örnek, <xref:System.Windows.Media.EllipseGeometry> nesnesinin <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliğine animasyon uygulamak için bir <xref:System.Windows.Media.Animation.PointAnimationUsingPath> kullanır.</span><span class="sxs-lookup"><span data-stu-id="c0339-107">The example uses a <xref:System.Windows.Media.Animation.PointAnimationUsingPath> to animate the <xref:System.Windows.Media.EllipseGeometry> object's <xref:System.Windows.Media.EllipseGeometry.Center%2A> property.</span></span>  
  
 [!code-xaml[PathAnimationGallery_snippet#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_snippet/CS/pointanimationusingpathexample.xaml#pointanimationusingpathwholepage)]  
  
 [!code-csharp[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/CSharp/PointAnimationUsingPathExample.cs#pointanimationusingpathwholepage)]
 [!code-vb[PathAnimationGallery_procedural_snip#PointAnimationUsingPathWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PathAnimationGallery_procedural_snip/VisualBasic/PointAnimationUsingPathExample.vb#pointanimationusingpathwholepage)]  
  
 <span data-ttu-id="c0339-108">Tüm örnek için bkz. [yol animasyon örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span><span class="sxs-lookup"><span data-stu-id="c0339-108">For the complete sample, see [Path Animation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations).</span></span>  
  
 <span data-ttu-id="c0339-109">Önceki örneğin kod sürümü, yalnızca bir animasyon uygulanmış olsa da <xref:System.Windows.Media.EllipseGeometry>hareketlendirmek için bir <xref:System.Windows.Media.Animation.Storyboard> kullandı.</span><span class="sxs-lookup"><span data-stu-id="c0339-109">The code version of the preceding sample used a <xref:System.Windows.Media.Animation.Storyboard> to animate the <xref:System.Windows.Media.EllipseGeometry>, even though only one animation was applied.</span></span> <span data-ttu-id="c0339-110"><xref:System.Windows.Media.Animation.Storyboard>, bu animasyonlar aynı <xref:System.Windows.Media.Animation.Storyboard>tarafından denetlenebildiğinden, genellikle birden çok animasyon uygulamanın en kolay yoludur.</span><span class="sxs-lookup"><span data-stu-id="c0339-110">A <xref:System.Windows.Media.Animation.Storyboard> is often the easiest way to apply multiple animations because these animations can be controlled by the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="c0339-111">Ancak, kod kullanırken bir özelliğe tek bir animasyon uygulamak için daha kolay bir yol <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi kullanmaktır.</span><span class="sxs-lookup"><span data-stu-id="c0339-111">However, an easier way to apply a single animation to a property when using code is to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method.</span></span> <span data-ttu-id="c0339-112">Bir örnek için bkz. [görsel taslak kullanmadan özelliğe animasyon ekleme](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="c0339-112">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0339-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0339-113">See also</span></span>

- [<span data-ttu-id="c0339-114">Yol animasyon örneği</span><span class="sxs-lookup"><span data-stu-id="c0339-114">Path Animation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/PathAnimations)
- [<span data-ttu-id="c0339-115">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="c0339-115">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="c0339-116">Yol Animasyonu ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c0339-116">Path Animation How-to Topics</span></span>](path-animation-how-to-topics.md)
