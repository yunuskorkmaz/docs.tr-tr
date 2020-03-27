---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344874"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="8586f-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="8586f-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="8586f-103">Bu örnek, <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> bir <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="8586f-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8586f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8586f-104">Example</span></span>  
 <span data-ttu-id="8586f-105">Aşağıdaki örnek, bir elipsi üçgen bir yol boyunca hareket ettirir.</span><span class="sxs-lookup"><span data-stu-id="8586f-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="8586f-106">Örnek, bir <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.Media.EllipseGeometry>. özelliğini canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="8586f-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="8586f-107">Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:</span><span class="sxs-lookup"><span data-stu-id="8586f-107">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="8586f-108">İlk yarı saniye boyunca, elipsi başlangıç konumundan sabit bir hızda bir yol boyunca taşımak için <xref:System.Windows.Media.Animation.LinearPointKeyFrame> sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8586f-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="8586f-109">Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearPointKeyFrame> doğrusal enterpolasyon oluşturmak gibi doğrusal anahtar çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="8586f-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="8586f-110">Sonraki yarım saniyenin sonunda, aniden bir <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> sonraki konuma yol boyunca elips taşımak için sınıfın bir örnek kullanır.</span><span class="sxs-lookup"><span data-stu-id="8586f-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="8586f-111">Değerler arasında ani <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar kareler.</span><span class="sxs-lookup"><span data-stu-id="8586f-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3. <span data-ttu-id="8586f-112">Son iki saniye boyunca, elipsi başlangıç konumuna geri taşımak için <xref:System.Windows.Media.Animation.SplinePointKeyFrame> sınıfın bir örneğini kullanır.</span><span class="sxs-lookup"><span data-stu-id="8586f-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="8586f-113">Özellik değerlerine <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplinePointKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="8586f-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="8586f-114">Bu örnekte, animasyon yavaş yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlar.</span><span class="sxs-lookup"><span data-stu-id="8586f-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="8586f-115">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="8586f-115">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="8586f-116">Diğer animasyon örnekleri ile tutarlılık için, bu örneğin <xref:System.Windows.Media.Animation.Storyboard> kod sürümleri <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>bir nesne uygulamak için kullanın.</span><span class="sxs-lookup"><span data-stu-id="8586f-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="8586f-117">Ancak, kod halinde tek bir animasyon uygularken, <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="8586f-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="8586f-118">Örneğin, Bir [Storyboard kullanmadan bir Özellik Animasyon](how-to-animate-a-property-without-using-a-storyboard.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="8586f-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8586f-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8586f-119">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="8586f-120">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8586f-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="8586f-121">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="8586f-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
