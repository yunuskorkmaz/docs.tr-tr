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
ms.openlocfilehash: 3ce7c1824dc53c154ba1091ea62c1b8950b757c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557569"
---
# <a name="easing-functions"></a><span data-ttu-id="0e640-102">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="0e640-102">Easing Functions</span></span>
<span data-ttu-id="0e640-103">Hareket hızı işlevleri, animasyonların özel matematiksel formüller olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="0e640-103">Easing functions allow you to apply custom mathematical formulas to your animations.</span></span> <span data-ttu-id="0e640-104">Örneğin, bir nesnenin gerçekçi Sıçrama veya dizinindeymiş gibi yay üzerinde davranır isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e640-104">For example, you may want an object to realistically bounce or behave as though it were on a spring.</span></span> <span data-ttu-id="0e640-105">Bu etkilerle yaklaşık için anahtar çerçeve veya From/To/By bile animasyonları kullanabilirsiniz, ancak iş önemli miktarda götürecek ve animasyon matematiksel formül kullanmaktan daha az doğru olacaktır.</span><span class="sxs-lookup"><span data-stu-id="0e640-105">You could use Key-Frame or even From/To/By animations to approximate these effects but it would take a significant amount of work and the animation would be less accurate than using a mathematical formula.</span></span>  
  
 <span data-ttu-id="0e640-106">Devralarak kendi özel hareket hızı işlevi oluşturma yanı sıra <xref:System.Windows.Media.Animation.EasingFunctionBase>, çalışma zamanı tarafından sağlanan çeşitli hareket hızı işlevlerini birini ortak efektleri oluşturmak için kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e640-106">Besides creating your own custom easing function by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>, you can use one of several easing functions provided by the runtime to create common effects.</span></span>  
  
-   <span data-ttu-id="0e640-107"><xref:System.Windows.Media.Animation.BackEase>: Bir animasyon hareketini biraz belirtilen yolda animasyon başlamadan önce geri çeker.</span><span class="sxs-lookup"><span data-stu-id="0e640-107"><xref:System.Windows.Media.Animation.BackEase>: Retracts the motion of an animation slightly before it begins to animate in the path indicated.</span></span>  
  
-   <span data-ttu-id="0e640-108"><xref:System.Windows.Media.Animation.BounceEase>: Sıçrama efekti oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e640-108"><xref:System.Windows.Media.Animation.BounceEase>: Creates a bouncing effect.</span></span>  
  
-   <span data-ttu-id="0e640-109"><xref:System.Windows.Media.Animation.CircleEase>: Bir döngüsel işlevi kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e640-109"><xref:System.Windows.Media.Animation.CircleEase>: Creates an animation that accelerates and/or decelerates using a circular function.</span></span>  
  
-   <span data-ttu-id="0e640-110"><xref:System.Windows.Media.Animation.CubicEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>3</sup>.</span><span class="sxs-lookup"><span data-stu-id="0e640-110"><xref:System.Windows.Media.Animation.CubicEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>3</sup>.</span></span>  
  
-   <span data-ttu-id="0e640-111"><xref:System.Windows.Media.Animation.ElasticEase>: Kalanına gelene kadar ve geriye salınım yapan yay benzer bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e640-111"><xref:System.Windows.Media.Animation.ElasticEase>: Creates an animation that resembles a spring oscillating back and forth until it comes to rest.</span></span>  
  
-   <span data-ttu-id="0e640-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Bir üstel formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e640-112"><xref:System.Windows.Media.Animation.ExponentialEase>: Creates an animation that accelerates and/or decelerates using an exponential formula.</span></span>  
  
-   <span data-ttu-id="0e640-113"><xref:System.Windows.Media.Animation.PowerEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>p</sup> p olduğu için eşit<xref:System.Windows.Media.Animation.PowerEase.Power%2A>özelliği.</span><span class="sxs-lookup"><span data-stu-id="0e640-113"><xref:System.Windows.Media.Animation.PowerEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>p</sup> where p is equal to the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span>  
  
-   <span data-ttu-id="0e640-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>2</sup>.</span><span class="sxs-lookup"><span data-stu-id="0e640-114"><xref:System.Windows.Media.Animation.QuadraticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>2</sup>.</span></span>  
  
-   <span data-ttu-id="0e640-115"><xref:System.Windows.Media.Animation.QuarticEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur *f*(*t*) = *t*<sup>4</sup>.</span><span class="sxs-lookup"><span data-stu-id="0e640-115"><xref:System.Windows.Media.Animation.QuarticEase>: Creates an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>4</sup>.</span></span>  
  
-   <span data-ttu-id="0e640-116"><xref:System.Windows.Media.Animation.QuinticEase>: Formülü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturmak *f*(*t*) = *t*<sup>5</sup>.</span><span class="sxs-lookup"><span data-stu-id="0e640-116"><xref:System.Windows.Media.Animation.QuinticEase>: Create an animation that accelerates and/or decelerates using the formula *f*(*t*) = *t*<sup>5</sup>.</span></span>  
  
-   <span data-ttu-id="0e640-117"><xref:System.Windows.Media.Animation.SineEase>: Bir sinüs formülünü kullanarak hızlandırır/yavaşlayan bir animasyon oluşturur.</span><span class="sxs-lookup"><span data-stu-id="0e640-117"><xref:System.Windows.Media.Animation.SineEase>: Creates an animation that accelerates and/or decelerates using a sine formula.</span></span>  
  
 <span data-ttu-id="0e640-118">Aşağıdaki örnek ile hareket hızı bu işlevlerin davranış keşfedebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e640-118">You can explore the behavior of these easing functions with the following sample.</span></span>  
  
 [<span data-ttu-id="0e640-119">Bu örneği çalıştırmak</span><span class="sxs-lookup"><span data-stu-id="0e640-119">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 <span data-ttu-id="0e640-120">Bir animasyon hareket hızı işlevi uygulamak için kullanmak `EasingFunction` animasyonun özellik animasyon uygulamak için hareket hızı işlevi belirtin.</span><span class="sxs-lookup"><span data-stu-id="0e640-120">To apply an easing function to an animation, use the `EasingFunction` property of the animation specify the easing function to apply to the animation.</span></span> <span data-ttu-id="0e640-121">Aşağıdaki örnek uygular bir <xref:System.Windows.Media.Animation.BounceEase> işlevine kolaylaştırma bir <xref:System.Windows.Media.Animation.DoubleAnimation> Sıçrama efekti oluşturmak için.</span><span class="sxs-lookup"><span data-stu-id="0e640-121">The following example applies a <xref:System.Windows.Media.Animation.BounceEase> easing function to a <xref:System.Windows.Media.Animation.DoubleAnimation> to create a bouncing effect.</span></span>  
  
 [<span data-ttu-id="0e640-122">Bu örneği çalıştırmak</span><span class="sxs-lookup"><span data-stu-id="0e640-122">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 <span data-ttu-id="0e640-123">Önceki örnekte, bir From/To/By için hareket hızı işlevi uygulandı animasyon.</span><span class="sxs-lookup"><span data-stu-id="0e640-123">In the previous example, the easing function was applied to a From/To/By animation.</span></span> <span data-ttu-id="0e640-124">Bu gibi durumlarda, bu hareket hızı işlevler aynı zamanda anahtar çerçeve animasyonları uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="0e640-124">You can also apply these easing functions to Key-Frame animations.</span></span> <span data-ttu-id="0e640-125">Aşağıdaki örnek anahtar çerçeveler ilişkili işlevler kolaylaştırma ile sözleşmeleri yukarı, yavaşlatır, ardından aşağı (düşüyor gibi) genişletir ve bir Dur geri dönmeler bir dikdörtgen bir animasyon oluşturmak için nasıl kullanılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e640-125">The following example shows how to use key frames with easing functions associated with them to create an animation of a rectangle that contracts upward, slows down, then expands downward (as though falling) and then bounces to a stop.</span></span>  
  
 [<span data-ttu-id="0e640-126">Bu örneği çalıştırmak</span><span class="sxs-lookup"><span data-stu-id="0e640-126">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 <span data-ttu-id="0e640-127">Kullanabileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> nasıl hareket hızı işlevi, diğer bir deyişle, davranacağını özelliğini değiştirin animasyonun nasıl ilişkilendirileceğini.</span><span class="sxs-lookup"><span data-stu-id="0e640-127">You can use the <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> property to alter how the easing function behaves, that is, change how the animation interpolates.</span></span> <span data-ttu-id="0e640-128">Verebileceğiniz üç olası değerler <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span><span class="sxs-lookup"><span data-stu-id="0e640-128">There are three possible values you can give for <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:</span></span>  
  
-   <span data-ttu-id="0e640-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: İlişkilendirme hareket hızı işlev ile ilişkili matematik formülünü takip eder.</span><span class="sxs-lookup"><span data-stu-id="0e640-129"><xref:System.Windows.Media.Animation.EasingMode.EaseIn>: Interpolation follows the mathematical formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="0e640-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: İlişkilendirme % 100'ü çıkış eksi hareket hızı işlev ile ilişkili formülün izler.</span><span class="sxs-lookup"><span data-stu-id="0e640-130"><xref:System.Windows.Media.Animation.EasingMode.EaseOut>: Interpolation follows 100% interpolation minus the output of the formula associated with the easing function.</span></span>  
  
-   <span data-ttu-id="0e640-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: İlişkilendirme kullanan <xref:System.Windows.Media.Animation.EasingMode.EaseIn> animasyonun ilk yarısı için ve <xref:System.Windows.Media.Animation.EasingMode.EaseOut> ikinci yarısı için.</span><span class="sxs-lookup"><span data-stu-id="0e640-131"><xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: Interpolation uses <xref:System.Windows.Media.Animation.EasingMode.EaseIn> for the first half of the animation and <xref:System.Windows.Media.Animation.EasingMode.EaseOut> for the second half.</span></span>  
  
 <span data-ttu-id="0e640-132">Grafikleri farklı değerlerini göstermek <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> nerede *f*(*x*) animasyon ilerlemesini gösterir ve *t* zamanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="0e640-132">The graphs below demonstrate the different values of <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> where *f*(*x*) represents the animation progress and *t* represents time.</span></span>  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 <span data-ttu-id="0e640-133">![BackEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-133">![BackEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 <span data-ttu-id="0e640-134">![BounceEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-134">![BounceEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 <span data-ttu-id="0e640-135">![CircleEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-135">![CircleEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 <span data-ttu-id="0e640-136">![CubicEase EasingMode grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-136">![CubicEase EasingMode graphs.](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 <span data-ttu-id="0e640-137">![Farklı gevşeme modlarının ile ElasticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-137">![ElasticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 <span data-ttu-id="0e640-138">![Farklı gevşeme modlarının ExponentialEase grafikleri. ] (../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-138">![ExponentialEase graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 <span data-ttu-id="0e640-139">![Farklı gevşeme modlarının ile QuarticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-139">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 <span data-ttu-id="0e640-140">![Farklı gevşeme modlarının grafikleriyle](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-140">![QuadraticEase with graphs of different easingmodes](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 <span data-ttu-id="0e640-141">![Farklı gevşeme modlarının ile QuarticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-141">![QuarticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 <span data-ttu-id="0e640-142">![Farklı gevşeme modlarının ile QuinticEase. ] (../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-142">![QuinticEase with graphs of different easingmodes.](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")</span></span>  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 <span data-ttu-id="0e640-143">![Farklı EasingMode değerleri için SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span><span class="sxs-lookup"><span data-stu-id="0e640-143">![SineEase for different EasingMode values](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e640-144">Kullanabileceğiniz <xref:System.Windows.Media.Animation.PowerEase> aynı davranışı oluşturmak için <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, ve <xref:System.Windows.Media.Animation.QuinticEase> kullanarak <xref:System.Windows.Media.Animation.PowerEase.Power%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="0e640-144">You can use <xref:System.Windows.Media.Animation.PowerEase> to create the same behavior as <xref:System.Windows.Media.Animation.CubicEase>, <xref:System.Windows.Media.Animation.QuadraticEase>, <xref:System.Windows.Media.Animation.QuarticEase>, and <xref:System.Windows.Media.Animation.QuinticEase> by using the <xref:System.Windows.Media.Animation.PowerEase.Power%2A> property.</span></span> <span data-ttu-id="0e640-145">Örneğin, kullanmak istediğiniz <xref:System.Windows.Media.Animation.PowerEase> yerine için <xref:System.Windows.Media.Animation.CubicEase>, belirtin bir <xref:System.Windows.Media.Animation.PowerEase.Power%2A> değeri 3.</span><span class="sxs-lookup"><span data-stu-id="0e640-145">For example, if you want to use <xref:System.Windows.Media.Animation.PowerEase> to substitute for <xref:System.Windows.Media.Animation.CubicEase>, specify a <xref:System.Windows.Media.Animation.PowerEase.Power%2A> value of 3.</span></span>  
  
 <span data-ttu-id="0e640-146">Çalışma zamanında dahil hareket hızı işlevlerini kullanmanın yanı sıra, kendi özel hareket hızı işlevler devralarak oluşturabileceğiniz <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span><span class="sxs-lookup"><span data-stu-id="0e640-146">In addition to using the easing functions included in the run-time, you can create your own custom easing functions by inheriting from <xref:System.Windows.Media.Animation.EasingFunctionBase>.</span></span> <span data-ttu-id="0e640-147">Aşağıdaki örnekte nasıl basit bir özel hareket hızı işlevin oluşturulacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="0e640-147">The following example demonstrates how to create a simple custom easing function.</span></span> <span data-ttu-id="0e640-148">Geçersiz kılarak hareket hızı işlevi nasıl davranacağını için kendi matematiksel mantığınızı ekleyebilirsiniz <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="0e640-148">You can add your own mathematical logic for how the easing function behaves by overriding the <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A> method.</span></span>  
  
 [<span data-ttu-id="0e640-149">Bu örneği çalıştırmak</span><span class="sxs-lookup"><span data-stu-id="0e640-149">Run this sample</span></span>](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
