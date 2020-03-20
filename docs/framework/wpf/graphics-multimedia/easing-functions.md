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
ms.openlocfilehash: a25bde5098af853c3906a174a189fc35f33f0525
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186493"
---
# <a name="easing-functions"></a><span data-ttu-id="91fdc-102">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="91fdc-102">Easing Functions</span></span>
<span data-ttu-id="91fdc-103">Kolaylaştırma işlevleri animasyonlarınıza özel matematiksel formüller uygulamanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="91fdc-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="91fdc-104">Örneğin, bir nesnenin gerçekçi bir şekilde sıçramasını veya bir yay üzerindeymiş gibi gibi gibi bir şekilde gibi bir şekilde</span><span class="sxs-lookup"><span data-stu-id="91fdc-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="91fdc-105">Bu efektleri yaklaşık olarak belirlemek için Anahtar Çerçeve'yi ve hatta Gelen/To/By animasyonlarını kullanabilirsiniz, ancak önemli miktarda çalışma gerekir ve animasyon matematiksel bir formül kullanmaktan daha az doğru olacaktır.</span><span class="sxs-lookup"><span data-stu-id="91fdc-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="91fdc-106">Devralarak kendi özel kolaylaştırma işlevi <xref:System.Windows.Media.Animation.EasingFunctionBase>oluşturmanın yanı sıra, ortak efektler oluşturmak için çalışma zamanı tarafından sağlanan birkaç kolaylaştırma işlevlerinden birini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91fdc-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
- <span data-ttu-id="91fdc-107"><xref:System.Windows.Media.Animation.BackEase>: Bir animasyonun hareketini, belirtilen yolda canlandırmaya başlamadan biraz önce geri çekilir.</span><span class="sxs-lookup"><span data-stu-id="91fdc-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
- <span data-ttu-id="91fdc-108"><xref:System.Windows.Media.Animation.BounceEase>: Zıplayan bir etki yaratır.</span><span class="sxs-lookup"><span data-stu-id="91fdc-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
- <span data-ttu-id="91fdc-109"><xref:System.Windows.Media.Animation.CircleEase>: Dairesel bir fonksiyon kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
- <span data-ttu-id="91fdc-110"><xref:System.Windows.Media.Animation.CubicEase>: *F*(*t*) = *t*<sup>3</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
- <span data-ttu-id="91fdc-111"><xref:System.Windows.Media.Animation.ElasticEase>: Dinlenmeye gelene kadar ileri geri salınım yapan bir yayı andıran bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
- <span data-ttu-id="91fdc-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Üstel bir formül kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
- <span data-ttu-id="91fdc-113"><xref:System.Windows.Media.Animation.PowerEase>: <xref:System.Windows.Media.Animation.PowerEase.Power%2A> *P'nin*özelliğe eşit olduğu f (*t*) = *t*<sup>p</sup> formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
- <span data-ttu-id="91fdc-114"><xref:System.Windows.Media.Animation.QuadraticEase>: *F*(*t*) = *t*<sup>2</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
- <span data-ttu-id="91fdc-115"><xref:System.Windows.Media.Animation.QuarticEase>: *F*(*t*) = *t*<sup>4</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
- <span data-ttu-id="91fdc-116"><xref:System.Windows.Media.Animation.QuinticEase>: *F*(*t*) = *t*<sup>5</sup>formüllerini kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturun.</span><span class="sxs-lookup"><span data-stu-id="91fdc-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
- <span data-ttu-id="91fdc-117"><xref:System.Windows.Media.Animation.SineEase>: Sinüs formülü kullanarak hızlandıran ve/veya yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="91fdc-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="91fdc-118">Animasyona kolaylaştırma işlevi uygulamak için `EasingFunction` animasyonun özelliğini kullanın animasyona uygulamak için kolaylaştırma işlevini belirtin.</span><span class="sxs-lookup"><span data-stu-id="91fdc-118">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="91fdc-119">Aşağıdaki örnek, zıplayan bir <xref:System.Windows.Media.Animation.BounceEase> <xref:System.Windows.Media.Animation.DoubleAnimation> etki oluşturmak için a'ya bir kolaylaştırma işlevi uygular.</span><span class="sxs-lookup"><span data-stu-id="91fdc-119">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [!code-xaml[BounceEase_snippet#BounceEase](~/samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="91fdc-120">Önceki örnekte, kolaylaştırma işlevi Bir Gelen/To/By animasyonuna uygulanmıştır.</span><span class="sxs-lookup"><span data-stu-id="91fdc-120">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="91fdc-121">Bu kolaylaştırma işlevlerini Anahtar Kare animasyonlarına da uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91fdc-121">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="91fdc-122">Aşağıdaki örnek, yukarı doğru küçülen, yavaşlayan, sonra aşağı doğru genişleyen (düşüyormuş gibi) ve sonra bir durağa seken bir dikdörtgenin animasyonu oluşturmak için kendileriyle ilişkili kolaylaştırma işlevlerine sahip anahtar çerçevelerin nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="91fdc-122">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](~/samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="91fdc-123">Özelliği, kolaylaştırma işlevinin nasıl çalıştığını değiştirmek, diğer bir şekilde animasyonun enterpolasyonunu değiştirmek için kullanabilirsiniz. <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A></span><span class="sxs-lookup"><span data-stu-id="91fdc-123">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="91fdc-124">Verebileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>üç olası değer vardır:</span><span class="sxs-lookup"><span data-stu-id="91fdc-124">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
- <span data-ttu-id="91fdc-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Enterpolasyon, kolaylaştırma fonksiyonu ile ilişkili matematiksel formülü izler.</span><span class="sxs-lookup"><span data-stu-id="91fdc-125"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="91fdc-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Enterpolasyon, kolaylaştırma fonksiyonu ile ilişkili formülün çıktısını eksi %100 enterpolasyon izler.</span><span class="sxs-lookup"><span data-stu-id="91fdc-126"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
- <span data-ttu-id="91fdc-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Enterpolasyon animasyonun ilk yarısı <xref:System.Windows.Media.Animation.EasingMode.EaseOut> ve ikinci yarısı için kullanır. <xref:System.Windows.Media.Animation.EasingMode.EaseIn></span><span class="sxs-lookup"><span data-stu-id="91fdc-127"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="91fdc-128">Aşağıdaki *grafikler, f*( <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> *x*) animasyon ilerlemesini ve *t'nin* zamanı temsil ettiği yerin farklı değerlerini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91fdc-128">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="91fdc-129">![BackEase EasingMode grafikleri.](./media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-129">![BackEase EasingMode graphs.](./media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="91fdc-130">![BounceEase EasingMode grafikleri.](./media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-130">![BounceEase EasingMode graphs.](./media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="91fdc-131">![CircleEase EasingMode grafikleri.](./media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-131">![CircleEase EasingMode graphs.](./media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="91fdc-132">![CubicEase EasingMode grafikleri.](./media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-132">![CubicEase EasingMode graphs.](./media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="91fdc-133">![ElasticEase farklı kolaylaştırma modları grafikleri ile.](./media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-133">![ElasticEase with graphs of different easingmodes.](./media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="91fdc-134">![Farklı kolaylaştırma modlarının üstelEase grafikleri.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-134">![ExponentialEase graphs of different easingmodes.](./media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="91fdc-135">![QuarticFarklı kolaylaştırma modları grafikleri ile kolaylaş.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-135">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="91fdc-136">![Farklı kolaylaştırma modlarının grafikleri ile QuadraticEase](./media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-136">![QuadraticEase with graphs of different easingmodes](./media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="91fdc-137">![QuarticFarklı kolaylaştırma modları grafikleri ile kolaylaş.](./media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-137">![QuarticEase with graphs of different easingmodes.](./media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="91fdc-138">![Farklı kolaylaştırma modları grafikleri ile QuinticEase.](./media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-138">![QuinticEase with graphs of different easingmodes.](./media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="91fdc-139">![Farklı EasingMode değerleri için SineEase](./media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="91fdc-139">![SineEase for different EasingMode values](./media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91fdc-140"><xref:System.Windows.Media.Animation.CubicEase>Aynı davranışı <xref:System.Windows.Media.Animation.PowerEase> oluşturmak için kullanabilirsiniz <xref:System.Windows.Media.Animation.QuadraticEase> <xref:System.Windows.Media.Animation.QuarticEase>, <xref:System.Windows.Media.Animation.QuinticEase> , , <xref:System.Windows.Media.Animation.PowerEase.Power%2A> ve özelliği kullanarak.</span><span class="sxs-lookup"><span data-stu-id="91fdc-140">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="91fdc-141">Örneğin, yerine kullanmak <xref:System.Windows.Media.Animation.PowerEase> <xref:System.Windows.Media.Animation.CubicEase>istiyorsanız, 3'ün <xref:System.Windows.Media.Animation.PowerEase.Power%2A> bir değerini belirtin.</span><span class="sxs-lookup"><span data-stu-id="91fdc-141">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="91fdc-142">Çalışma süresine dahil edilen kolaylaştırma işlevlerini kullanmanın yanı sıra, 'den <xref:System.Windows.Media.Animation.EasingFunctionBase>devralarak kendi özel kolaylaştırma işlevlerinizi oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91fdc-142">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="91fdc-143">Aşağıdaki örnek, basit bir özel kolaylaştırma işlevinin nasıl oluşturulabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="91fdc-143">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="91fdc-144">Kolaylaştırma işlevinin yöntemi geçersiz kılarak nasıl işlediğine <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> bağlı olarak kendi matematiksel mantığınızı ekleyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="91fdc-144">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](~/samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
