---
title: 'Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-fram animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 3a8e11ee8bfbbe87ca5a1c51b815dd21c124a951
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712031"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="5143f-102">Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="5143f-102">How to: Control Key-Frame Animation Timing</span></span>
<span data-ttu-id="5143f-103">Bu örnekte anahtar çerçeveler içinde bir anahtar çerçeve animasyonu zamanlamasını denetlemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="5143f-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="5143f-104">Diğer animasyonlar gibi anahtar-çerçeve animasyonlara sahip bir <xref:System.Windows.Media.Animation.Timeline.Duration%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="5143f-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="5143f-105">Bir animasyonun süresini belirtmeye ek olarak, hangi parçası bir bu süre her anahtar çerçeveler için ayrılan belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="5143f-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="5143f-106">Zamanı paylaştırmak için belirttiğiniz bir <xref:System.Windows.Media.Animation.KeyTime> her anahtar kare animasyon için.</span><span class="sxs-lookup"><span data-stu-id="5143f-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>  
  
 <span data-ttu-id="5143f-107"><xref:System.Windows.Media.Animation.KeyTime> Her anahtar çerçevesi (Bu belirtmiyor bir anahtar kare oynatıldığında sürenin uzunluğunu) bir anahtar kare bittiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="5143f-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="5143f-108">Belirtebileceğiniz bir <xref:System.Windows.Media.Animation.KeyTime> olarak bir <xref:System.TimeSpan> değeri, bir yüzdesi olarak veya <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> özel değeri.</span><span class="sxs-lookup"><span data-stu-id="5143f-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5143f-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="5143f-109">Example</span></span>  
 <span data-ttu-id="5143f-110">Aşağıdaki örnekte bir <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ekranda bir dikdörtgene animasyon ekleme için.</span><span class="sxs-lookup"><span data-stu-id="5143f-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="5143f-111">Anahtar çerçeveler anahtar zaman ayarlanır <xref:System.TimeSpan> değerleri.</span><span class="sxs-lookup"><span data-stu-id="5143f-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
 [!code-vb[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
 [!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]  
  
 <span data-ttu-id="5143f-112">Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5143f-112">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="5143f-113">![Anahtar değerlerini 3, 4 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="5143f-113">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>  
  
 <span data-ttu-id="5143f-114">Anahtar çerçeveler anahtar zaman yüzde değerleri ile ayarlanan dışında aynı olan bir animasyon sonraki örnekte gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="5143f-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
 [!code-vb[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
 [!code-xaml[keyframes_snip#KeyTimesPercentageExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]  
  
 <span data-ttu-id="5143f-115">Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5143f-115">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="5143f-116">![Anahtar değerlerini 3, 4 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="5143f-116">![Key values are reached at 3, 4, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>  
  
 <span data-ttu-id="5143f-117">Sonraki örnekte <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> anahtar saat değerleri.</span><span class="sxs-lookup"><span data-stu-id="5143f-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
 [!code-vb[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
 [!code-xaml[keyframes_snip#KeyTimesUniformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]  
  
 <span data-ttu-id="5143f-118">Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5143f-118">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="5143f-119">![Anahtar değerlerini 3.3,6.6 ve 9,9 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="5143f-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>  
  
 <span data-ttu-id="5143f-120">Son örnekte <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar saat değerleri.</span><span class="sxs-lookup"><span data-stu-id="5143f-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>  
  
 [!code-csharp[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
 [!code-vb[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
 [!code-xaml[keyframes_snip#KeyTimesPacedExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]  
  
 <span data-ttu-id="5143f-121">Her bir anahtar kare değerini erişildiğinde, aşağıdaki şekilde gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="5143f-121">The following illustration shows when the value of each key frame is reached.</span></span>  
  
 <span data-ttu-id="5143f-122">![Anahtar değerler 0, 5 ve 10 saniyede tamamladı](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="5143f-122">![Key values are reached at 0, 5, and 10 seconds](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>  
  
 <span data-ttu-id="5143f-123">Kolaylık olması için bu örnek yerel animasyonları kullanır, kod sürümlerini değil film şeritleri, yalnızca tek bir animasyonu tek bir özelliğe uygulanmakta olduğu, ancak örnekler, film şeritleri kullanmayı değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="5143f-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="5143f-124">Kod içinde bir film şeridini bildirmeyi gösteren bir örnek için bkz: [görsel taslak kullanarak özelliğe animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="5143f-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).</span></span>  
  
 <span data-ttu-id="5143f-125">Tam bir örnek için bkz. [ana kare animasyon örnek](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="5143f-125">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span> <span data-ttu-id="5143f-126">Anahtar çerçeve animasyonları hakkında daha fazla bilgi için bkz. [anahtar-çerçeve animasyonlara genel bakış](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="5143f-126">For more information about key frame animations, see the [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5143f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5143f-127">See also</span></span>
- [<span data-ttu-id="5143f-128">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="5143f-128">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="5143f-129">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="5143f-129">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="5143f-130">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="5143f-130">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
