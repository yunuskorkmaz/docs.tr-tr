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
ms.openlocfilehash: 7940d65c61d57ec9c6a2a6e02e3b1e3e0bb2795f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610480"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a><span data-ttu-id="2a9f2-102">Nasıl yapılır: AnimationClock Kullanarak Bir Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="2a9f2-102">How to: Animate a Property by Using an AnimationClock</span></span>
<span data-ttu-id="2a9f2-103">Bu örnek nasıl kullanılacağını gösterir <xref:System.Windows.Media.Animation.Clock> özelliği oynatmak nesneleri.</span><span class="sxs-lookup"><span data-stu-id="2a9f2-103">This example shows how to use <xref:System.Windows.Media.Animation.Clock> objects to animate a property.</span></span>  
  
 <span data-ttu-id="2a9f2-104">Bağımlılık özelliği için üç yol vardır:</span><span class="sxs-lookup"><span data-stu-id="2a9f2-104">There are three ways to animate a dependency property:</span></span>  
  
-   <span data-ttu-id="2a9f2-105">Oluşturma bir <xref:System.Windows.Media.Animation.AnimationTimeline> bu özellik ile ilişkilendirin kullanılarak bir <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="2a9f2-105">Create an <xref:System.Windows.Media.Animation.AnimationTimeline> and associate it with that property by using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span>  
  
-   <span data-ttu-id="2a9f2-106">Nesnenin kullanın <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemi tek bir uygulamaya <xref:System.Windows.Media.Animation.AnimationTimeline> için target özelliği.</span><span class="sxs-lookup"><span data-stu-id="2a9f2-106">Use the object's <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method to apply a single <xref:System.Windows.Media.Animation.AnimationTimeline> to a target property.</span></span>  
  
-   <span data-ttu-id="2a9f2-107">Oluşturma bir <xref:System.Windows.Media.Animation.AnimationClock> gelen bir <xref:System.Windows.Media.Animation.AnimationTimeline> ve bir özelliğe uygulayın.</span><span class="sxs-lookup"><span data-stu-id="2a9f2-107">Create an <xref:System.Windows.Media.Animation.AnimationClock> from an <xref:System.Windows.Media.Animation.AnimationTimeline> and apply it to a property.</span></span>  
  
 <span data-ttu-id="2a9f2-108"><xref:System.Windows.Media.Animation.Storyboard> nesneleri ve <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> yöntemini etkinleştirmek, doğrudan oluşturmadan ve dağıtmadan saatler özelliklerine animasyon uygulamak (örnekler için bkz [görsel taslak kullanarak özelliğe animasyon ekleme](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) ve [bir özelliği olmadan animasyon ekleme Görsel taslak kullanarak](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); Storyboard ve sizin için otomatik olarak dağıtılmış.</span><span class="sxs-lookup"><span data-stu-id="2a9f2-108"><xref:System.Windows.Media.Animation.Storyboard> objects and the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method enable you to animate properties without directly creating and distributing clocks (for examples, see [Animate a Property by Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) and [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); clocks are created and distributed for you automatically.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a9f2-109">Örnek</span><span class="sxs-lookup"><span data-stu-id="2a9f2-109">Example</span></span>  
 <span data-ttu-id="2a9f2-110">Aşağıdaki örnek nasıl oluşturulacağını gösterir. bir <xref:System.Windows.Media.Animation.AnimationClock> ve iki benzer özellikleri için geçerlidir.</span><span class="sxs-lookup"><span data-stu-id="2a9f2-110">The following example shows how to create an <xref:System.Windows.Media.Animation.AnimationClock> and apply it to two similar properties.</span></span>  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 <span data-ttu-id="2a9f2-111">Etkileşimli olarak denetleme gösteren bir örnek için bir <xref:System.Windows.Media.Animation.Clock> başladıktan sonra bkz [etkileşimli olarak saat denetimi](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span><span class="sxs-lookup"><span data-stu-id="2a9f2-111">For an example showing how to interactively control a <xref:System.Windows.Media.Animation.Clock> after it starts, see [Interactively Control a Clock](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a9f2-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a9f2-112">See also</span></span>
- [<span data-ttu-id="2a9f2-113">Görsel Taslak Kullanarak Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="2a9f2-113">Animate a Property by Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)
- [<span data-ttu-id="2a9f2-114">Görsel Taslak Kullanmadan Özelliğe Animasyon Ekleme</span><span class="sxs-lookup"><span data-stu-id="2a9f2-114">Animate a Property Without Using a Storyboard</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)
- [<span data-ttu-id="2a9f2-115">Özellik Animasyon Tekniklerine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="2a9f2-115">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
