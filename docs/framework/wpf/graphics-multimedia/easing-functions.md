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
ms.openlocfilehash: 72118711dfd40ad8c665157e09f01c60085db903
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965728"
---
# <a name="easing-functions"></a><span data-ttu-id="5d8f5-102">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="5d8f5-102">Easing Functions</span></span>
<span data-ttu-id="5d8f5-103">Kolaylaştırıcı işlevler, animasyonlarınız için özel matematik formülleri uygulamanıza olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="5d8f5-104">Örneğin, bir nesnenin bir yay üzerinde olmasına rağmen gerçekçi bir şekilde sıçramasını veya davranmasını isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="5d8f5-105">Bu etkileri tahmin etmek, ancak önemli miktarda iş yapmak ve animasyon matematiksel bir formül kullanmaktan daha az doğru olması için, anahtar çerçevesini veya bunlara ait/-/-by animasyonlarını kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="5d8f5-106">' Dan <xref:System.Windows.Media.Animation.EasingFunctionBase>devralarak kendi özel kolaylaştırıcı işlevinizi oluşturmanın yanı sıra, ortak efektler oluşturmak için çalışma zamanı tarafından sunulan birkaç kolaylaştırıcı işlevden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="5d8f5-107"><xref:System.Windows.Media.Animation.BackEase>: Bir animasyonun hareketini, belirtilen yoldaki animasyon başlamadan önce biraz daha geri çeker.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="5d8f5-108"><xref:System.Windows.Media.Animation.BounceEase>: Sıçrama efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="5d8f5-109"><xref:System.Windows.Media.Animation.CircleEase>: Döngüsel bir işlevi kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="5d8f5-110"><xref:System.Windows.Media.Animation.CubicEase>: *F*(*t*) = *t*<sup>3</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="5d8f5-111"><xref:System.Windows.Media.Animation.ElasticEase>: Rest 'e gelene kadar yay ve geri getirme durumuna benzeyen bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="5d8f5-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Üstel bir formülü kullanarak hızlanan/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="5d8f5-113"><xref:System.Windows.Media.Animation.PowerEase>: P 'nin özelliğe<xref:System.Windows.Media.Animation.PowerEase.Power%2A> eşit olduğu *f*(*t*) = *t*<sup>p</sup> formülünü kullanarak hızlanan ve/veya yavaşlalayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="5d8f5-114"><xref:System.Windows.Media.Animation.QuadraticEase>: *F*(*t*) = *t*<sup>2</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="5d8f5-115"><xref:System.Windows.Media.Animation.QuarticEase>: *F*(*t*) = *t*<sup>4</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="5d8f5-116"><xref:System.Windows.Media.Animation.QuinticEase>: *F*(*t*) = *t*<sup>5</sup>formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturun.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="5d8f5-117"><xref:System.Windows.Media.Animation.SineEase>: Bir sinüs formülünü kullanarak hızlanan/veya yavaşlalayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="5d8f5-118">Bir animasyona bir kolaylaştırıcı işlev uygulamak için animasyon `EasingFunction` özelliğini kullanın animasyon için uygulanacak kolaylaştırıcı işlevi belirtin.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="5d8f5-119">Aşağıdaki örnek, bir sıçrama <xref:System.Windows.Media.Animation.BounceEase> efekti oluşturmak için bir <xref:System.Windows.Media.Animation.DoubleAnimation> için bir kolaylaştırıcı işlev uygular.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="5d8f5-120">Önceki örnekte, kolaylaştırıcı işlev From/To/By animasyonuna uygulandı.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="5d8f5-121">Bu kolaylaştırıcı işlevleri, anahtar çerçeve animasyonlarına da uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="5d8f5-122">Aşağıdaki örnek, yukarı doğru sözleşme yapan bir dikdörtgenin animasyonunu oluşturmak için kendileriyle ilişkili kolaylaştırıcı işlevlerle anahtar çerçevelerini nasıl kullanacağınızı gösterir, yavaşlatır ve sonra da bir duruma geri rayın.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="5d8f5-123"><xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> Özelliğini kullanarak, kolaylaştırıcı işlevin nasıl davranacağını, yani animasyonun nasıl ilişkilendirileceğini değiştirme şeklini değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="5d8f5-124">İçin <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>verebileceğiniz üç olası değer vardır:</span><span class="sxs-lookup"><span data-stu-id="5d8f5-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="5d8f5-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Enterpolasyon, kolaylaştırıcı işlevle ilişkili matematik formülünü izler.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="5d8f5-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: İlişkilendirme,% 100 ilişkilendirme ile kolaylaştırıcı işlevle ilişkili formülün çıkışının% ' u izler.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="5d8f5-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: İlişkilendirme animasyonun <xref:System.Windows.Media.Animation.EasingMode.EaseIn> ilk yarısında ve <xref:System.Windows.Media.Animation.EasingMode.EaseOut> ikinci yarı için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="5d8f5-128">Aşağıdaki grafikler, *f*(*x*) uygulamasının <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> animasyon ilerlemesini temsil ettiği farklı değerleri gösterir ve *t* süreyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="5d8f5-129">![Backealıneasingmode grafikleri.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="5d8f5-130">![BounceEase EasingMode grafikleri.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="5d8f5-131">![CircleEase EasingMode grafikleri.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="5d8f5-132">![Küıease EasingMode grafikleri.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="5d8f5-133">![Farklı easingmodes grafikleriyle ElasticEase.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="5d8f5-134">![Farklı easingmodes 'ın üs ALease grafikleri.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="5d8f5-135">![Farklı easingmodes grafikleriyle Kutıa.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="5d8f5-136">![Farklı easingmodes grafikleriyle Quadratısonu](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="5d8f5-137">![Farklı easingmodes grafikleriyle Kutıa.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="5d8f5-138">![Farklı easingmodes grafikleriyle Qubaşlatılmadı.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="5d8f5-139">![Farklı EasingMode değerleri Için SineEase](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="5d8f5-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5d8f5-140"><xref:System.Windows.Media.Animation.PowerEase> <xref:System.Windows.Media.Animation.CubicEase> Özelliğinikullanarak<xref:System.Windows.Media.Animation.QuarticEase>, ,,<xref:System.Windows.Media.Animation.QuinticEase> ve ile aynı davranışı oluşturmak için kullanabilirsiniz. <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.PowerEase.Power%2A></span><span class="sxs-lookup"><span data-stu-id="5d8f5-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="5d8f5-141">Örneğin, <xref:System.Windows.Media.Animation.PowerEase> <xref:System.Windows.Media.Animation.PowerEase.Power%2A> yerine koymak için kullanmak istiyorsanız ,3değerinibelirtin.<xref:System.Windows.Media.Animation.CubicEase></span><span class="sxs-lookup"><span data-stu-id="5d8f5-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="5d8f5-142">Çalışma zamanında dahil olan kolaylaştırıcı işlevleri kullanmanın yanı sıra, ' dan <xref:System.Windows.Media.Animation.EasingFunctionBase>devralarak kendi özel kolaylaştırıcı işlevlerinizi de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="5d8f5-143">Aşağıdaki örnek, basit bir özel kolaylaştırıcı işlevin nasıl oluşturulacağını göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="5d8f5-144"><xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> Yöntemini geçersiz kılarak kolaylaştırıcı işlevin nasıl davrandığı için kendi matematik mantığınızı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="5d8f5-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>   
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
