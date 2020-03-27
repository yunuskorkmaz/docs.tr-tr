---
title: 'Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], timing
- timing key-frame animation
ms.assetid: b059216f-7d4b-4ca8-a019-bc287ee7bf16
ms.openlocfilehash: 8cfd2be0bbc526ed92a5fb1b558a5a41dc9c3113
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344730"
---
# <a name="how-to-control-key-frame-animation-timing"></a><span data-ttu-id="ceb7b-102">Nasıl yapılır: Anahtar Çerçeve Animasyonu Zamanlamasını Denetleme</span><span class="sxs-lookup"><span data-stu-id="ceb7b-102">How to: Control Key-Frame Animation Timing</span></span>

<span data-ttu-id="ceb7b-103">Bu örnek, anahtar kare animasyonu içindeki anahtar karelerin zamanlamasını nasıl denetler, gösterir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-103">This example shows how to control the timing of key frames within a key-frame animation.</span></span> <span data-ttu-id="ceb7b-104">Diğer animasyonlar gibi, anahtar kare <xref:System.Windows.Media.Animation.Timeline.Duration%2A> animasyonların da bir özelliği vardır.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-104">Like other animations, key-frame animations have a <xref:System.Windows.Media.Animation.Timeline.Duration%2A> property.</span></span> <span data-ttu-id="ceb7b-105">Animasyonun süresini belirtmenin yanı sıra, bu sürenin her bir anahtar çerçevesine hangi bölümünün ayrılmış olduğunu belirtmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-105">In addition to specifying the duration of an animation, you need to specify what part of that duration is allotted to each of its key frames.</span></span> <span data-ttu-id="ceb7b-106">Zamanı tahsis etmek için, <xref:System.Windows.Media.Animation.KeyTime> animasyondaki her anahtar kare için bir tane belirtirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-106">To allot the time, you specify a <xref:System.Windows.Media.Animation.KeyTime> for each key frame in the animation.</span></span>

<span data-ttu-id="ceb7b-107">Her <xref:System.Windows.Media.Animation.KeyTime> anahtar kare için bir anahtar çerçevesi sona erdiğinde belirtilir (bir anahtar çerçevesi çalış süresini belirtmez).</span><span class="sxs-lookup"><span data-stu-id="ceb7b-107">The <xref:System.Windows.Media.Animation.KeyTime> for each key frame specifies when a key frame ends (it does not specify the length of time a key frame plays).</span></span> <span data-ttu-id="ceb7b-108">Bir <xref:System.Windows.Media.Animation.KeyTime> <xref:System.TimeSpan> değeri bir değer olarak, yüzde olarak <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> veya <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> özel değer olarak belirtebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-108">You can specify a <xref:System.Windows.Media.Animation.KeyTime> as a <xref:System.TimeSpan> value, as a percentage, or as the <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> or <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> special value.</span></span>

## <a name="example"></a><span data-ttu-id="ceb7b-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="ceb7b-109">Example</span></span>

<span data-ttu-id="ceb7b-110">Aşağıdaki örnekte, <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> ekran daki bir dikdörtgeni canlandırmak için a kullanır.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-110">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> to animate a rectangle across the screen.</span></span> <span data-ttu-id="ceb7b-111">Anahtar çerçevelerin anahtar süreleri değerlerle <xref:System.TimeSpan> ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-111">The key frames' key times are set with <xref:System.TimeSpan> values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimestimespanexample)]
[!code-vb[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimestimespanexample)]
[!code-xaml[keyframes_snip#KeyTimesTimeSpanExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimestimespanexample)]

<span data-ttu-id="ceb7b-112">Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-112">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ceb7b-113">![Anahtar değerlere 3, 4 ve 10 saniyede ulaşılır](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span><span class="sxs-lookup"><span data-stu-id="ceb7b-113">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime1-timespan.png "graphicsmm_keyframe_keytime1_timespan")</span></span>

<span data-ttu-id="ceb7b-114">Sonraki örnekte, anahtar çerçevelerin anahtar süreleri yüzde değerleriyle ayarlanan dışında, aynı olan bir animasyon gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-114">The next example shows an animation that is identical, except that the key frames' key times are set with percentage values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespercentageexample)]
[!code-vb[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespercentageexample)]
[!code-xaml[keyframes_snip#KeyTimesPercentageExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespercentageexample)]

<span data-ttu-id="ceb7b-115">Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-115">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ceb7b-116">![Anahtar değerlere 3, 4 ve 10 saniyede ulaşılır](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span><span class="sxs-lookup"><span data-stu-id="ceb7b-116">![Key values are reached at 3, 4, and 10 seconds](./media/graphicsmm-keyframe-keytime2-percentage.png "graphicsmm_keyframe_keytime2_percentage")</span></span>

<span data-ttu-id="ceb7b-117">Sonraki örnekanahtar <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> zaman değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-117">The next example uses <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimesuniformexample)]
[!code-vb[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimesuniformexample)]
[!code-xaml[keyframes_snip#KeyTimesUniformExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimesuniformexample)]

<span data-ttu-id="ceb7b-118">Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-118">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ceb7b-119">![Anahtar değerlere 3.3,6.6 ve 9.9 saniye olarak ulaşılır](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span><span class="sxs-lookup"><span data-stu-id="ceb7b-119">![Key values are reached at 3.3,6.6, and 9.9 seconds](./media/graphicsmm-keyframe-keytime3-uniform.png "graphicsmm_keyframe_keytime3_uniform")</span></span>

<span data-ttu-id="ceb7b-120">Son örnek, <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> anahtar zaman değerlerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-120">The final example uses <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> key time values.</span></span>

[!code-csharp[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/KeyTimesExample.cs#keytimespacedexample)]
[!code-vb[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/keytimesexample.vb#keytimespacedexample)]
[!code-xaml[keyframes_snip#KeyTimesPacedExample](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/KeyTimesExample.xaml#keytimespacedexample)]

<span data-ttu-id="ceb7b-121">Aşağıdaki resimde, her anahtar çerçevenin değerine ne zaman ulaşıldığı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-121">The following illustration shows when the value of each key frame is reached.</span></span>

<span data-ttu-id="ceb7b-122">![Anahtar değerlere 0, 5 ve 10 saniyede ulaşılır](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span><span class="sxs-lookup"><span data-stu-id="ceb7b-122">![Key values are reached at 0, 5, and 10 seconds](./media/graphicsmm-keyframe-keytime4-paced.png "graphicsmm_keyframe_keytime4_paced")</span></span>

<span data-ttu-id="ceb7b-123">Basitlik için, bu örneğin kod sürümleri, yalnızca tek bir animasyon tek bir özelliğe uygulandığından, film şeridi değil, yerel animasyonlar kullanır, ancak örnekler bunun yerine film şeridi kullanmak üzere değiştirilebilir.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-123">For simplicity, the code versions of this example use local animations, not storyboards, because only a single animation is being applied to a single property, but the examples may be modified to use storyboards instead.</span></span> <span data-ttu-id="ceb7b-124">Bir film şeridinin kod da nasıl bildirilen bir örnek için, [Storyboard kullanarak Bir Özellik Animasyon'a](how-to-animate-a-property-by-using-a-storyboard.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-124">For an example showing how to declare a storyboard in code, see [Animate a Property by Using a Storyboard](how-to-animate-a-property-by-using-a-storyboard.md).</span></span>

<span data-ttu-id="ceb7b-125">Tam örnek için [Anahtar Çerçeve Animasyon Örneği'ne](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation)bakın.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-125">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span> <span data-ttu-id="ceb7b-126">Anahtar kare animasyonları hakkında daha fazla bilgi için [Anahtar Kare Animasyonlarına Genel Bakış'a](key-frame-animations-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-126">For more information about key frame animations, see the [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ceb7b-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ceb7b-127">See also</span></span>

- [<span data-ttu-id="ceb7b-128">Anahtar-Çerçeve Animasyonlara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="ceb7b-128">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="ceb7b-129">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="ceb7b-129">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="ceb7b-130">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="ceb7b-130">How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
