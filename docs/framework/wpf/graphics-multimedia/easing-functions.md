---
title: Kolaylaştırıcı İşlevler
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 456308e37bddc1df86b49085139a3810c4959a58
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354511"
---
# <a name="easing-functions"></a><span data-ttu-id="8554b-102">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="8554b-102">Easing Functions</span></span>
<span data-ttu-id="8554b-103">Kolaylaştırıcı işlevler özel matematik formülleri animasyonlarınızda uygulamanıza izin verir.</span><span class="sxs-lookup"><span data-stu-id="8554b-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="8554b-104">Örneğin, bir nesnenin gerçekçi Sıçrama veya işlevmiş gibi üzerinde spring davranır isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8554b-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="8554b-105">Bu etkilerle yaklaşık olarak belirlemenizi sağlayan anahtar-çerçeve veya bile gelen/için/göre animasyonlarına kullanabilirsiniz, ancak iş önemli miktarda götürecek ve animasyon matematiksel bir formül kullanmaktan daha az doğru olacaktır.</span><span class="sxs-lookup"><span data-stu-id="8554b-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="8554b-106">Kendi özel hızlandırma işlevini devralarak oluşturma yanı sıra <xref:System.Windows.Media.Animation.EasingFunctionBase>, ortak efektleri oluşturmak için çalışma zamanı tarafından sağlanan çeşitli kolaylaştırıcı işlevler birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8554b-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="8554b-107"><xref:System.Windows.Media.Animation.BackEase>: Belirtilen yolda animasyon uygulamak başlamadan önce bir animasyon hareket biraz geri çeker.</span><span class="sxs-lookup"><span data-stu-id="8554b-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="8554b-108"><xref:System.Windows.Media.Animation.BounceEase>: Sıçrama efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8554b-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="8554b-109"><xref:System.Windows.Media.Animation.CircleEase>: Döngüsel işlevi kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8554b-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="8554b-110"><xref:System.Windows.Media.Animation.CubicEase>: Formülü kullanarak yavaşlayan hızlanan bir animasyon oluşturur *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="8554b-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="8554b-111"><xref:System.Windows.Media.Animation.ElasticEase>: Kalanına gelene kadar ve geriye salınım yapan bir spring benzer bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8554b-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="8554b-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Bir üstel formülünü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8554b-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="8554b-113"><xref:System.Windows.Media.Animation.PowerEase>: Formülü kullanarak yavaşlayan hızlanan bir animasyon oluşturur *f*(*t*) = *t*<sup>p</sup> p olduğu için eşit<xref:System.Windows.Media.Animation.PowerEase.Power%2A>özelliği.</span><span class="sxs-lookup"><span data-stu-id="8554b-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="8554b-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Formülü kullanarak yavaşlayan hızlanan bir animasyon oluşturur *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="8554b-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="8554b-115"><xref:System.Windows.Media.Animation.QuarticEase>: Formülü kullanarak yavaşlayan hızlanan bir animasyon oluşturur *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="8554b-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="8554b-116"><xref:System.Windows.Media.Animation.QuinticEase>: Formül kullanarak yavaşlayan hızlandırır animasyon oluşturmak *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="8554b-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="8554b-117"><xref:System.Windows.Media.Animation.SineEase>: Sinüs formülü kullanarak yavaşlayan hızlandırır animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8554b-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="8554b-118">Animasyonlara kolaylaştırıcı bir işlev uygulamak için `EasingFunction` özelliğine animasyon uygulamak üzere kolaylaştırıcı işlevi belirtin.</span><span class="sxs-lookup"><span data-stu-id="8554b-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="8554b-119">Aşağıdaki örnek geçerli bir <xref:System.Windows.Media.Animation.BounceEase> kolaylaştırıcı işlevi bir <xref:System.Windows.Media.Animation.DoubleAnimation> Sıçrama efekti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="8554b-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="8554b-120">Önceki örnekte, bir From/To/By için hızlandırma işlevini uygulandığı animasyon.</span><span class="sxs-lookup"><span data-stu-id="8554b-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="8554b-121">Anahtar-çerçeve animasyonlara kolaylaştırıcı bu işlevler de uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8554b-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="8554b-122">Aşağıdaki örnek anahtar çerçeveler ile ilişkili kolaylaştırıcı işlevleri sözleşmeler yukarı, yavaşlatır, ardından aşağı doğru (düşüyor gibi) genişletir ve ardından Durma noktasına geri dönmeler bir dikdörtgen bir animasyon oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8554b-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="8554b-123">Kullanabileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> özelliğini hızlandırma işlevini, diğer bir deyişle, davranış biçimini değiştirmek için değiştirme animasyonun nasıl ilişkilendirileceğini.</span><span class="sxs-lookup"><span data-stu-id="8554b-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="8554b-124">Verebileceğiniz üç olası değer vardır <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="8554b-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="8554b-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: İlişkilendirme ile hızlandırma işlevini ilişkili matematik formülünü izler.</span><span class="sxs-lookup"><span data-stu-id="8554b-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="8554b-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: İlişkilendirme % 100'ü eksi kolaylaştırıcı bir işlev ile ilişkili formülün izler.</span><span class="sxs-lookup"><span data-stu-id="8554b-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="8554b-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: İlişkilendirme kullanan <xref:System.Windows.Media.Animation.EasingMode.EaseIn> animasyonun ilk yarısında ve <xref:System.Windows.Media.Animation.EasingMode.EaseOut> ikinci yarısında hiç.</span><span class="sxs-lookup"><span data-stu-id="8554b-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="8554b-128">Farklı değerleri aşağıdaki grafikleri gösteren <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> burada *f*(*x*) animasyon ilerleme durumunu temsil eder ve *t* saati temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8554b-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="8554b-129">![BackEase EasingMode grafikleri. ](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="8554b-130">![BounceEase EasingMode grafikleri. ](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="8554b-131">![CircleEase EasingMode grafikleri. ](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="8554b-132">![CubicEase EasingMode grafikleri. ](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="8554b-133">![ElasticEase farklı gevşeme modlarının ile. ](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="8554b-134">![ExponentialEase grafiklerini farklı gevşeme modlarının. ](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="8554b-135">![QuarticEase farklı gevşeme modlarının ile. ](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="8554b-136">![Farklı gevşeme modlarının grafikleriyle](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="8554b-137">![QuarticEase farklı gevşeme modlarının ile. ](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="8554b-138">![QuinticEase farklı gevşeme modlarının ile. ](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="8554b-139">![Farklı EasingMode değerler için SineEase](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="8554b-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8554b-140">Kullanabileceğiniz <xref:System.Windows.Media.Animation.PowerEase> aynı davranışı oluşturmak için <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, ve <xref:System.Windows.Media.Animation.QuinticEase> kullanarak <xref:System.Windows.Media.Animation.PowerEase.Power%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="8554b-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="8554b-141">Örneğin, kullanmak istediğiniz <xref:System.Windows.Media.Animation.PowerEase> için yedek olarak <xref:System.Windows.Media.Animation.CubicEase>, belirtin bir <xref:System.Windows.Media.Animation.PowerEase.Power%2A> 3 değeri.</span><span class="sxs-lookup"><span data-stu-id="8554b-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="8554b-142">Kolaylaştırıcı işlevler çalışma zamanı içinde bulunan kullanmanın yanı sıra, kendi özel kolaylaştırıcı işlevler devralarak oluşturabilirsiniz <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="8554b-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="8554b-143">Aşağıdaki örnek, basit bir özel hızlandırma işlevini nasıl oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="8554b-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="8554b-144">Geçersiz kılarak hızlandırma işlevini nasıl davranacağını kendi matematiksel mantığı ekleyebileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="8554b-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
