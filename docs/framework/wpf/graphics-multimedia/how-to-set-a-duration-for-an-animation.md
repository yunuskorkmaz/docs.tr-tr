---
title: 'Nasıl yapılır: Animasyon için Süre Ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: bdae1689ffeb8c54d756b9debbd26d57a052892d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651161"
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="e9404-102">Nasıl yapılır: Animasyon için Süre Ayarlama</span><span class="sxs-lookup"><span data-stu-id="e9404-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="e9404-103">A <xref:System.Windows.Media.Animation.Timeline> zaman bir segmentini ve kesiminin uzunluğu çizelgesinin tarafından belirlenir temsil <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="e9404-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="e9404-104">Olduğunda bir <xref:System.Windows.Media.Animation.Timeline> geçerlilik süresinin, yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="e9404-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="e9404-105">Varsa <xref:System.Windows.Media.Animation.Timeline> alt öğe zaman çizelgeleri varsa bunlar da yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="e9404-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="e9404-106">Bir animasyon, söz konusu olduğunda <xref:System.Windows.Duration> animasyon bitiş değeri başlangıç değerinden geçişin ne kadar alacağını belirtir.</span><span class="sxs-lookup"><span data-stu-id="e9404-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="e9404-107">Belirtebileceğiniz bir <xref:System.Windows.Duration> belirli, sınırlı bir süre veya özel değerler <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="e9404-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="e9404-108">Bir animasyon zaman sonlu uzunluğu olması gerektiğinden bir animasyonun süresi bir saat değeri her zaman olmalıdır; aksi takdirde, animasyon hedef değerleri arasında geçiş yapma bilmez.</span><span class="sxs-lookup"><span data-stu-id="e9404-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="e9404-109">Kapsayıcı zaman çizelgeleri (<xref:System.Windows.Media.Animation.TimelineGroup> nesneleri), gibi <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>, varsayılan süre olan <xref:System.Windows.Duration.Automatic%2A>, bunlar otomatik olarak sonlandırmak son alt öğe yürütme durdurulduğunda anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="e9404-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="e9404-110">Aşağıdaki örnekte, genişlik, yükseklik ve dolgu rengi içinde bir <xref:System.Windows.Shapes.Rectangle> bir animasyon görünür.</span><span class="sxs-lookup"><span data-stu-id="e9404-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="e9404-111">Süreleri, animasyon efektleri algılanan animasyonun hızını denetleme ve alt öğe zaman çizelgelerini süresi kapsayıcı zaman çizelgesinin süresiyle geçersiz kılma dahil olmak üzere sonuçta animasyon ve kapsayıcı zaman çizelgesi üzerinde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="e9404-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e9404-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="e9404-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="e9404-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9404-113">See also</span></span>

- <xref:System.Windows.Duration>
- [<span data-ttu-id="e9404-114">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="e9404-114">Animation Overview</span></span>](animation-overview.md)
