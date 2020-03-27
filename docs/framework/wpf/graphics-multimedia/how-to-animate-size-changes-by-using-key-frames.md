---
title: 'Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344649"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="6638e-102">Nasıl yapılır: Anahtar Çerçeveler Kullanarak Boyut Değişikliklerine Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="6638e-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="6638e-103">Bu örnek, anahtar kareler kullanarak boyut değişikliklerini nasıl canlandıracaklarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="6638e-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6638e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="6638e-104">Example</span></span>  
 <span data-ttu-id="6638e-105">Aşağıdaki örnek, <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> bir <xref:System.Windows.Media.ArcSegment>. özelliğini <xref:System.Windows.Media.ArcSegment.Size%2A> canlandırmak için sınıfı kullanır.</span><span class="sxs-lookup"><span data-stu-id="6638e-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="6638e-106">Bu animasyon aşağıdaki şekilde üç anahtar kare kullanır:</span><span class="sxs-lookup"><span data-stu-id="6638e-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="6638e-107">Animasyonun ilk yarısında, yavaş yavaş yay <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> boyutunu artırmak için sınıfın bir örnek kullanır. Değerler arasında düzgün <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> doğrusal geçiş oluşturma gibi doğrusal anahtar çerçeveler.</span><span class="sxs-lookup"><span data-stu-id="6638e-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="6638e-108">Sonraki yarım saniyenin sonunda, aniden yay <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> boyutunu artırmak için sınıfın bir örnek kullanır. Değerler arasında ani <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> sıçramalar oluşturmak gibi ayrık anahtar çerçeveleri, yani boyut değişiklikleri aniden oluşur ve ince değildir.</span><span class="sxs-lookup"><span data-stu-id="6638e-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="6638e-109">Son iki saniye içinde, yay <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> boyutunu artırmak için sınıfın bir örneğini kullanır. Özellik değerlerine <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> göre <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> değerler arasında değişken bir geçiş oluşturmak gibi spline anahtar çerçeveleri.</span><span class="sxs-lookup"><span data-stu-id="6638e-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="6638e-110">Bu örnekte, yay boyutu ilk başta yavaş yavaş artar ve daha sonra zaman diliminin sonuna doğru katlanarak artar.</span><span class="sxs-lookup"><span data-stu-id="6638e-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="6638e-111">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="6638e-111">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6638e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6638e-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="6638e-113">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="6638e-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="6638e-114">Anahtar Çerçeve ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="6638e-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
