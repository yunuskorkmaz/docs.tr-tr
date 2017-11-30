---
title: "Nasıl yapılır: bildirim almak, bir saat &#39; s durum değişiklikleri"
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
- clocks [WPF], notification of state changes
- notifications [WPF], clocks' state changes
ms.assetid: ecb10fc9-d0c2-45c3-b0a1-7b11baa733da
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f59fddb1add29d52ccba6fc8b8ce84938b53a1c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-receive-notification-when-a-clock39s-state-changes"></a><span data-ttu-id="f00c8-102">Nasıl yapılır: bildirim almak, bir saat &#39; s durum değişiklikleri</span><span class="sxs-lookup"><span data-stu-id="f00c8-102">How to: Receive Notification When a Clock&#39;s State Changes</span></span>
<span data-ttu-id="f00c8-103">Saatin <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> olayı oluşur, kendi <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> zaman saatin başlatıldığında veya durdurulduğunda gibi geçersiz hale gelir.</span><span class="sxs-lookup"><span data-stu-id="f00c8-103">A clock's <xref:System.Windows.Media.Animation.Clock.CurrentStateInvalidated> event occurs when its <xref:System.Windows.Media.Animation.Clock.CurrentState%2A> becomes invalid, such as when the clock starts or stops.</span></span> <span data-ttu-id="f00c8-104">Kullanarak doğrudan ile bu olay için kaydedebilirsiniz bir <xref:System.Windows.Media.Animation.Clock>, veya kullanarak kaydolabilirsiniz bir <xref:System.Windows.Media.Animation.Timeline>.</span><span class="sxs-lookup"><span data-stu-id="f00c8-104">You can register for this event with directly using a <xref:System.Windows.Media.Animation.Clock>, or you can register using a <xref:System.Windows.Media.Animation.Timeline>.</span></span>  
  
 <span data-ttu-id="f00c8-105">Aşağıdaki örnekte, bir <xref:System.Windows.Media.Animation.Storyboard> ve iki <xref:System.Windows.Media.Animation.DoubleAnimation> nesnesi iki dikdörtgen genişliğini animasyon için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f00c8-105">In the following example, a <xref:System.Windows.Media.Animation.Storyboard> and two <xref:System.Windows.Media.Animation.DoubleAnimation> objects are used to animate the width of two rectangles.</span></span> <span data-ttu-id="f00c8-106"><xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> Olay saat durum değişikliklerini dinlemek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="f00c8-106">The <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event is used to listen for clock state changes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f00c8-107">Örnek</span><span class="sxs-lookup"><span data-stu-id="f00c8-107">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#_graphicsmm_StateExampleMarkupWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml#_graphicsmm_stateexamplemarkupwholepage)]  
  
 [!code-csharp[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/StateExample.xaml.cs#_graphicsmm_stateeventhandlers)]
 [!code-vb[timingbehaviors_snip#_graphicsmm_StateEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_snip/visualbasic/stateexample.xaml.vb#_graphicsmm_stateeventhandlers)]  
  
 <span data-ttu-id="f00c8-108">Aşağıdaki çizimde animasyonların farklı durumlara girin üst zaman çizelgesi gösterir (*film şeridi*) ilerler.</span><span class="sxs-lookup"><span data-stu-id="f00c8-108">The following illustration shows the different states the animations enter as the parent timeline (*Storyboard*) progresses.</span></span>  
  
 <span data-ttu-id="f00c8-109">![Film şeridi iki animasyon için durumlar saat](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span><span class="sxs-lookup"><span data-stu-id="f00c8-109">![Clock states for a Storyboard with two animations](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-3timelines.png "graphicsmm_3timelines")</span></span>  
  
 <span data-ttu-id="f00c8-110">Aşağıdaki tabloda kez aktarılma gösterir *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay ateşlenir:</span><span class="sxs-lookup"><span data-stu-id="f00c8-110">The following table shows the times at which *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||  
|-|-|-|-|-|-|-|  
|<span data-ttu-id="f00c8-111">Süre (saniye)</span><span class="sxs-lookup"><span data-stu-id="f00c8-111">Time (Seconds)</span></span>|<span data-ttu-id="f00c8-112">1.</span><span class="sxs-lookup"><span data-stu-id="f00c8-112">1</span></span>|<span data-ttu-id="f00c8-113">10</span><span class="sxs-lookup"><span data-stu-id="f00c8-113">10</span></span>|<span data-ttu-id="f00c8-114">19</span><span class="sxs-lookup"><span data-stu-id="f00c8-114">19</span></span>|<span data-ttu-id="f00c8-115">21</span><span class="sxs-lookup"><span data-stu-id="f00c8-115">21</span></span>|<span data-ttu-id="f00c8-116">30</span><span class="sxs-lookup"><span data-stu-id="f00c8-116">30</span></span>|<span data-ttu-id="f00c8-117">39</span><span class="sxs-lookup"><span data-stu-id="f00c8-117">39</span></span>|  
|<span data-ttu-id="f00c8-118">Durum</span><span class="sxs-lookup"><span data-stu-id="f00c8-118">State</span></span>|<span data-ttu-id="f00c8-119">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-119">Active</span></span>|<span data-ttu-id="f00c8-120">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-120">Active</span></span>|<span data-ttu-id="f00c8-121">Durduruldu</span><span class="sxs-lookup"><span data-stu-id="f00c8-121">Stopped</span></span>|<span data-ttu-id="f00c8-122">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-122">Active</span></span>|<span data-ttu-id="f00c8-123">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-123">Active</span></span>|<span data-ttu-id="f00c8-124">Durduruldu</span><span class="sxs-lookup"><span data-stu-id="f00c8-124">Stopped</span></span>|  
  
 <span data-ttu-id="f00c8-125">Aşağıdaki tabloda kez aktarılma gösterir *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay ateşlenir:</span><span class="sxs-lookup"><span data-stu-id="f00c8-125">The following table shows the times at which *Animation2*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires:</span></span>  
  
||||||||||  
|-|-|-|-|-|-|-|-|-|  
|<span data-ttu-id="f00c8-126">Süre (saniye)</span><span class="sxs-lookup"><span data-stu-id="f00c8-126">Time (Seconds)</span></span>|<span data-ttu-id="f00c8-127">1.</span><span class="sxs-lookup"><span data-stu-id="f00c8-127">1</span></span>|<span data-ttu-id="f00c8-128">9</span><span class="sxs-lookup"><span data-stu-id="f00c8-128">9</span></span>|<span data-ttu-id="f00c8-129">11</span><span class="sxs-lookup"><span data-stu-id="f00c8-129">11</span></span>|<span data-ttu-id="f00c8-130">19</span><span class="sxs-lookup"><span data-stu-id="f00c8-130">19</span></span>|<span data-ttu-id="f00c8-131">21</span><span class="sxs-lookup"><span data-stu-id="f00c8-131">21</span></span>|<span data-ttu-id="f00c8-132">29</span><span class="sxs-lookup"><span data-stu-id="f00c8-132">29</span></span>|<span data-ttu-id="f00c8-133">31</span><span class="sxs-lookup"><span data-stu-id="f00c8-133">31</span></span>|<span data-ttu-id="f00c8-134">39</span><span class="sxs-lookup"><span data-stu-id="f00c8-134">39</span></span>|  
|<span data-ttu-id="f00c8-135">Durum</span><span class="sxs-lookup"><span data-stu-id="f00c8-135">State</span></span>|<span data-ttu-id="f00c8-136">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-136">Active</span></span>|<span data-ttu-id="f00c8-137">Doldurma</span><span class="sxs-lookup"><span data-stu-id="f00c8-137">Filling</span></span>|<span data-ttu-id="f00c8-138">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-138">Active</span></span>|<span data-ttu-id="f00c8-139">Durduruldu</span><span class="sxs-lookup"><span data-stu-id="f00c8-139">Stopped</span></span>|<span data-ttu-id="f00c8-140">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-140">Active</span></span>|<span data-ttu-id="f00c8-141">Doldurma</span><span class="sxs-lookup"><span data-stu-id="f00c8-141">Filling</span></span>|<span data-ttu-id="f00c8-142">Etkin</span><span class="sxs-lookup"><span data-stu-id="f00c8-142">Active</span></span>|<span data-ttu-id="f00c8-143">Durduruldu</span><span class="sxs-lookup"><span data-stu-id="f00c8-143">Stopped</span></span>|  
  
 <span data-ttu-id="f00c8-144">Dikkat *Animation1*'s <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> olay harekete 10 saniyede durumuna kalsa bile <xref:System.Windows.Media.Animation.ClockState.Active>.</span><span class="sxs-lookup"><span data-stu-id="f00c8-144">Notice that *Animation1*'s  <xref:System.Windows.Media.Animation.Timeline.CurrentStateInvalidated> event fires at 10 seconds, even though its state remains <xref:System.Windows.Media.Animation.ClockState.Active>.</span></span> <span data-ttu-id="f00c8-145">Durumu 10 saniyede değişti, ancak bunu değiştirildi çünkü <xref:System.Windows.Media.Animation.ClockState.Active> için <xref:System.Windows.Media.Animation.ClockState.Filling> ve ardından yeniden <xref:System.Windows.Media.Animation.ClockState.Active> aynı değer çizgilerinin içinde.</span><span class="sxs-lookup"><span data-stu-id="f00c8-145">That's because its state changed at 10 seconds, but it changed from <xref:System.Windows.Media.Animation.ClockState.Active> to <xref:System.Windows.Media.Animation.ClockState.Filling> and then back to <xref:System.Windows.Media.Animation.ClockState.Active> in the same tick.</span></span>
