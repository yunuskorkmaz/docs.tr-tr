---
title: "Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f574f85a5840e8bbe2d6c026d57a4cc28bd8a797
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="4ebd7-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak bir Noktaya Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="4ebd7-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="4ebd7-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> animasyon sınıfı bir <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ebd7-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4ebd7-104">Example</span></span>  
 <span data-ttu-id="4ebd7-105">Aşağıdaki örnek elips üçgen yol boyunca taşır.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="4ebd7-106">Örnek kullanır <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> animasyon sınıfı <xref:System.Windows.Media.EllipseGeometry.Center%2A> özelliği bir <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="4ebd7-107">Bu animasyon üç ana kare aşağıdaki şekilde kullanır:</span><span class="sxs-lookup"><span data-stu-id="4ebd7-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="4ebd7-108">Birinci yarım saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.LinearPointKeyFrame> elips yol boyunca bir hızda başlangıç konumundan taşımak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="4ebd7-109">Gibi doğrusal anahtar çerçeveler <xref:System.Windows.Media.Animation.LinearPointKeyFrame> değerler arasında yumuşak doğrusal bir ilişkilendirme oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="4ebd7-110">Sonraki son sırasında yarım ikinci bir örneğini kullanır <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> elips yol boyunca sonraki konumuna aniden taşımak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="4ebd7-111">Gibi ayrık anahtar çerçeveler <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> değerler arasında ani atlar oluşturun.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="4ebd7-112">Son iki saniye boyunca bir örneğini kullanan <xref:System.Windows.Media.Animation.SplinePointKeyFrame> elips başlangıç konumuna geri taşımak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="4ebd7-113">Gibi Eğri anahtar çerçeveler <xref:System.Windows.Media.Animation.SplinePointKeyFrame> değerlerine göre değerler arasında değişken geçiş oluşturmak <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="4ebd7-114">Bu örnekte, animasyon yavaş başlar ve zaman diliminin sonuna doğru katlanarak hızlanır.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="4ebd7-115">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="4ebd7-115">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="4ebd7-116">Diğer animasyon örnekleriyle tutarlılık için bu örnek kodu sürümlerini kullanan bir <xref:System.Windows.Media.Animation.Storyboard> uygulanacak nesne <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="4ebd7-117">Ancak, kodda tek bir animasyonu uygularken, bunu kullanmak daha basittir <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> kullanmak yerine yöntemi bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="4ebd7-118">Bir örnek için bkz: [özelliği olmadan kullanarak bir film şeridi animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="4ebd7-118">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ebd7-119">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4ebd7-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [<span data-ttu-id="4ebd7-120">Anahtar çerçeve animasyonları genel bakış</span><span class="sxs-lookup"><span data-stu-id="4ebd7-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="4ebd7-121">Anahtar çerçeve nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="4ebd7-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
