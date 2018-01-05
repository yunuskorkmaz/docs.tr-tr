---
title: "Nasıl yapılır: Animasyon için Süre Ayarlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e8d15a1b8432b3dae5bee73396bdec9fc9d50f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="c40be-102">Nasıl yapılır: Animasyon için Süre Ayarlama</span><span class="sxs-lookup"><span data-stu-id="c40be-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="c40be-103">A <xref:System.Windows.Media.Animation.Timeline> zaman kesimini ve bu kesimin uzunluğu zaman çizelgesinin tarafından belirlenir temsil <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="c40be-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="c40be-104">Zaman bir <xref:System.Windows.Media.Animation.Timeline> sonuna ulaşıldığında süresinin, yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="c40be-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="c40be-105">Varsa <xref:System.Windows.Media.Animation.Timeline> alt zaman çizelgeleri varsa bunlar da yürütmeyi durdurur.</span><span class="sxs-lookup"><span data-stu-id="c40be-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="c40be-106">Animasyonun, söz konusu olduğunda <xref:System.Windows.Duration> animasyon geçiş bitiş değeri başlangıç değerinden gereken süreyi belirtir.</span><span class="sxs-lookup"><span data-stu-id="c40be-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="c40be-107">Belirleyebileceğiniz bir <xref:System.Windows.Duration> belirli, sınırlı bir süre veya özel değerler ile <xref:System.Windows.Duration.Automatic%2A> veya <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="c40be-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="c40be-108">Animasyonun her zaman bir sonlu uzunluğu olması gerektiğinden animasyonun süresi her zaman bir saat değeri olmalıdır; aksi takdirde, animasyonun hedef değerler arasında geçiş yapma bilmez.</span><span class="sxs-lookup"><span data-stu-id="c40be-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="c40be-109">Kapsayıcı zaman çizelgeleri (<xref:System.Windows.Media.Animation.TimelineGroup> nesneler), aşağıdaki gibi <xref:System.Windows.Media.Animation.Storyboard> ve <xref:System.Windows.Media.Animation.ParallelTimeline>, varsayılan süre olan sahip <xref:System.Windows.Duration.Automatic%2A>, bunlar otomatik olarak sona kendi son alt çalma durduğunda anlamına gelir.</span><span class="sxs-lookup"><span data-stu-id="c40be-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="c40be-110">Aşağıdaki örnekte, genişlik, yükseklik ve dolgu rengini içinde bir <xref:System.Windows.Shapes.Rectangle> animasyon eklenir.</span><span class="sxs-lookup"><span data-stu-id="c40be-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="c40be-111">Süreleri animasyon efektleri animasyonun algılanan hızına denetleme ve kapsayıcı zaman çizelgesi süresini alt zaman çizelgeleri süresiyle geçersiz kılma gibi sonuçta animasyon ve kapsayıcı zaman çizelgeleri ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="c40be-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c40be-112">Örnek</span><span class="sxs-lookup"><span data-stu-id="c40be-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="c40be-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c40be-113">See Also</span></span>  
 <xref:System.Windows.Duration>  
 [<span data-ttu-id="c40be-114">Animasyona Genel bakış</span><span class="sxs-lookup"><span data-stu-id="c40be-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
