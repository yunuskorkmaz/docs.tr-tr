---
title: "Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme"
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
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 252da422ffb34e5865a29112e349e18d0f40327f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="67871-102">Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="67871-102">How to: Control Key-Frame Animation Timing</span></span>
<span data-ttu-id="67871-103">Bu örnek, içinde bir anahtar çerçeve animasyon ana kare zamanlamasını denetlemek gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67871-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="67871-104">Diğer animasyonları gibi anahtar çerçeve animasyonları sahip bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="67871-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="67871-105">Animasyonun süresini belirtmeye ek olarak, bu süre hangi kısmının her anahtar çerçeveleri ayrılan belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="67871-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="67871-106">Zamanı paylaştırmak için belirttiğiniz bir <xref:System.Windows.Media.Animation.KeyTime> animasyonun her anahtar çerçevede için.</span><span class="sxs-lookup"><span data-stu-id="67871-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>  
  
 <span data-ttu-id="67871-107"><xref:System.Windows.Media.Animation.KeyTime> Her anahtar çerçeve (bunu belirtmiyor anahtar çerçevesi oynadığı süre) bir anahtar çerçevesi bittiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="67871-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="67871-108">Belirleyebileceğiniz bir <xref:System.Windows.Media.Animation.KeyTime> olarak bir <xref:System.TimeSpan> değeri, bir yüzdesi olarak veya <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> özel değer.</span><span class="sxs-lookup"><span data-stu-id="67871-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67871-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="67871-109">Example</span></span>  
 <span data-ttu-id="67871-110">Aşağıdaki örnek kullanan bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> dikdörtgen ekranda animasyon eklemek için.</span><span class="sxs-lookup"><span data-stu-id="67871-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="67871-111">Anahtar çerçeveler anahtar kez ayarlanır <xref:System.TimeSpan> değerleri.</span><span class="sxs-lookup"><span data-stu-id="67871-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 <span data-ttu-id="67871-112">Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67871-112">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="67871-113">![Anahtar değerlerinin 3, 4 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="67871-113">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>  
  
 <span data-ttu-id="67871-114">Sonraki örnek anahtar çerçeveler anahtar zamanlarını yüzde değerlerle ayarlamak dışında aynı olan bir animasyon gösterir.</span><span class="sxs-lookup"><span data-stu-id="67871-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 <span data-ttu-id="67871-115">Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67871-115">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="67871-116">![Anahtar değerlerinin 3, 4 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="67871-116">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>  
  
 <span data-ttu-id="67871-117">Sonraki örnek kullanır <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> anahtar zaman değerlerini.</span><span class="sxs-lookup"><span data-stu-id="67871-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 <span data-ttu-id="67871-118">Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67871-118">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="67871-119">![3.3,6.6 ve 9,9 saniyede anahtar değerleri üst sınırına](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="67871-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>  
  
 <span data-ttu-id="67871-120">Son örnek kullanan <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar zaman değerlerini.</span><span class="sxs-lookup"><span data-stu-id="67871-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 <span data-ttu-id="67871-121">Her anahtar çerçeve değerini erişildiğinde, aşağıdaki çizimde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="67871-121">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="67871-122">![Anahtar değerleri 0, 5 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="67871-122">![Key values are reached at 0, 5, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>  
  
 <span data-ttu-id="67871-123">Kolaylık olması için bu örnek yerel animasyonları kullanır, kod sürümleri değil film şeritleri, çünkü yalnızca tek bir animasyonu tek bir özelliğe uygulanan ancak örnekler film şeritleri kullanmayı değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="67871-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="67871-124">Kodda film şeridi bildirmeyi gösteren bir örnek için bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="67871-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="67871-125">Tam bir örnek için bkz: [ana kare animasyon örneği](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="67871-125">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span> <span data-ttu-id="67871-126">Anahtar çerçeve animasyonları hakkında daha fazla bilgi için bkz: [anahtar çerçeve animasyonları genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="67871-126">For more information about key frame animations, see the [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67871-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="67871-127">See Also</span></span>  
 [<span data-ttu-id="67871-128">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="67871-128">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="67871-129">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="67871-129">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="67871-130">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="67871-130">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
