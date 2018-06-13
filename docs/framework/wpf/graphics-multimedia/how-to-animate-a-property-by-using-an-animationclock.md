---
title: 'Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: b8c64586d0dc5dc2e565fe4cb002e0f9cd4109af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558738"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="d11c3-102">Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="d11c3-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="d11c3-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Clock> bir özellik animasyon nesnelere.</span><span class="sxs-lookup"><span data-stu-id="d11c3-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="d11c3-104">Bağımlılık özelliği için üç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="d11c3-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="d11c3-105">Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve kullanarak bu özellik ile ilişkilendirin bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="d11c3-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="d11c3-106">Nesnenin kullanmak <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> tek bir uygulamak için yöntemi <xref:System.Windows.Media.Animation.AnimationTimeline> hedef özelliği.</span><span class="sxs-lookup"><span data-stu-id="d11c3-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="d11c3-107">Oluşturma bir <xref:System.Windows.Media.Animation.AnimationClock> gelen bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve bir özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="d11c3-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="d11c3-108"><xref:System.Windows.Media.Animation.Storyboard> nesneleri ve <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi doğrudan oluşturmadan ve saatler dağıtmadan özelliklerine animasyon olanak tanır (örnekler için bkz: [film şeridi kullanarak bir özelliği animasyon](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ve [bir özelliği olmadan animasyon ekleme Film şeridi kullanarak](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); Saatler oluşturulan ve sizin için otomatik olarak dağıtılır.</span><span class="sxs-lookup"><span data-stu-id="d11c3-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d11c3-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="d11c3-109">Example</span></span>  
 <span data-ttu-id="d11c3-110">Aşağıdaki örnekte nasıl oluşturulacağını gösterir bir <xref:System.Windows.Media.Animation.AnimationClock> ve iki benzer özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="d11c3-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="d11c3-111">Etkileşimli olarak denetleme gösteren bir örnek için bir <xref:System.Windows.Media.Animation.Clock> başladıktan sonra bkz [etkileşimli olarak saat denetimi](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="d11c3-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d11c3-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d11c3-112">See Also</span></span>  
 [<span data-ttu-id="d11c3-113">Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="d11c3-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [<span data-ttu-id="d11c3-114">Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="d11c3-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [<span data-ttu-id="d11c3-115">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="d11c3-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
