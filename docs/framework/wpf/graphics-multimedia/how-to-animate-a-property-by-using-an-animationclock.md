---
title: "Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme"
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
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 47df7aaad45000bc8c761a9bb9022d37e0f0828c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="c02d4-102">Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="c02d4-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="c02d4-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Clock> bir özellik animasyon nesnelere.</span><span class="sxs-lookup"><span data-stu-id="c02d4-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="c02d4-104">Bağımlılık özelliği için üç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="c02d4-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="c02d4-105">Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve kullanarak bu özellik ile ilişkilendirin bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="c02d4-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="c02d4-106">Nesnenin kullanmak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> tek bir uygulamak için yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> hedef özelliği.</span><span class="sxs-lookup"><span data-stu-id="c02d4-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="c02d4-107">Oluşturma bir <xref:System.Windows.Media.Animation.AnimationClock> gelen bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve bir özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="c02d4-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="c02d4-108"><xref:System.Windows.Media.Animation.Storyboard>nesneleri ve <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi doğrudan oluşturmadan ve saatler dağıtmadan özelliklerine animasyon olanak tanır (örnekler için bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ve [bir özelliği olmadan animasyon ekleme Film şeridi kullanarak](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); Saatler oluşturulan ve sizin için otomatik olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="c02d4-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c02d4-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="c02d4-109">Example</span></span>  
 <span data-ttu-id="c02d4-110">Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.Animation.AnimationClock> ve iki benzer özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="c02d4-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="c02d4-111">Etkileşimli olarak denetleme gösteren bir örnek için bir <xref:System.Windows.Media.Animation.Clock> başladıktan sonra bkz [etkileşimli olarak saat denetimi](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="c02d4-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c02d4-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c02d4-112">See Also</span></span>  
 [<span data-ttu-id="c02d4-113">Film şeridi kullanarak bir özelliği animasyon ekleme</span><span class="sxs-lookup"><span data-stu-id="c02d4-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="c02d4-114">Film şeridi kullanmadan bir özellik animasyon ekleme</span><span class="sxs-lookup"><span data-stu-id="c02d4-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [<span data-ttu-id="c02d4-115">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="c02d4-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
