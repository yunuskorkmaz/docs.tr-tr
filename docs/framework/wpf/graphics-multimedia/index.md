---
title: Grafikler ve Multimedya
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
ms.openlocfilehash: ecc54ad9453343f6306b0133fa180abd0db46f82
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596428"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="dd124-102">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="dd124-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="dd124-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]Çoklu ortam, vektör grafikleri, animasyon ve içerik oluşturma desteği sunarak geliştiricilerin ilginç kullanıcı arabirimlerini ve içerikleri oluşturmasını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="dd124-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="dd124-104">Visual Studio 'yu kullanarak vektör grafikleri veya karmaşık animasyonlar oluşturabilir ve bu ortamları uygulamalarınızla tümleştirin.</span><span class="sxs-lookup"><span data-stu-id="dd124-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="dd124-105">Bu konuda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , uygulamalarınıza grafikler, geçiş efektleri, ses ve video eklemenize olanak sağlayan grafik, animasyon ve medya özellikleri tanıtılmaktadır.</span><span class="sxs-lookup"><span data-stu-id="dd124-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="dd124-106">Windows hizmetinde WPF türlerinin kullanılması kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="dd124-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="dd124-107">Windows hizmetinde WPF türlerini kullanmaya çalışırsanız, hizmet beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="dd124-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="dd124-108">WPF 4 ' te grafik ve multimedya yenilikleri</span><span class="sxs-lookup"><span data-stu-id="dd124-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="dd124-109">Grafiklerle ve animasyonlarla ilgili çeşitli değişiklikler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="dd124-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="dd124-110">Düzen yuvarlama</span><span class="sxs-lookup"><span data-stu-id="dd124-110">Layout Rounding</span></span>

  <span data-ttu-id="dd124-111">Bir nesne kenarı bir piksel cihazının ortasında yer alıyorsa, DPı bağımsız grafik sistemi bulanık veya yarı saydam kenarlar gibi işleme yapıtları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="dd124-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="dd124-112">WPF 'nin önceki sürümleri, bu durumu işlemeye yardımcı olmak için piksel yaslaması içerir.</span><span class="sxs-lookup"><span data-stu-id="dd124-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="dd124-113">Silverlight 2 ' de, öğelerin tam piksel sınırlarına dönüşecek şekilde öğeleri taşımanın başka bir yolu olan düzen yuvarlama sunuldu.</span><span class="sxs-lookup"><span data-stu-id="dd124-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="dd124-114">WPF artık ekli özelliği olan düzen yuvarlamayı desteklemektedir <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> <xref:System.Windows.FrameworkElement> .</span><span class="sxs-lookup"><span data-stu-id="dd124-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="dd124-115">Önbelleğe alınmış bileşim</span><span class="sxs-lookup"><span data-stu-id="dd124-115">Cached Composition</span></span>

  <span data-ttu-id="dd124-116">Yeni <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıflarını kullanarak görsel ağacın karmaşık bir bölümünü bit eşlem olarak önbelleğe alabilir ve büyük ölçüde işleme süresini geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd124-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="dd124-117">Bit eşlem, fare tıklamaları gibi kullanıcı girişine yanıt vermeye devam eder ve tıpkı herhangi bir fırçayla tıpkı diğer öğelere de boyayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd124-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="dd124-118">Pixel Shader 3 desteği</span><span class="sxs-lookup"><span data-stu-id="dd124-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="dd124-119">WPF 4, <xref:System.Windows.Media.Effects.ShaderEffect> uygulamaların Pixel Shader (PS) sürüm 3,0 ' i kullanarak etkileri yazmasına izin vererek wpf 3,5 SP1 'de sunulan desteğin en üstünde oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="dd124-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="dd124-120">PS 3,0 gölgelendirici modeli PS 2,0 ' den daha karmaşıktır ve desteklenen donanımlar üzerinde daha da fazla etkiye olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="dd124-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="dd124-121">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="dd124-121">Easing Functions</span></span>

  <span data-ttu-id="dd124-122">Animasyonların davranışları üzerinde size ek denetim sağlayan kolaylaştırıcı işlevlerle animasyonları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd124-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="dd124-123">Örneğin, <xref:System.Windows.Media.Animation.ElasticEase> animasyona bir spriny davranışı vermek için bir animasyon uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd124-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="dd124-124">Daha fazla bilgi için bkz <xref:System.Windows.Media.Animation> . ad alanındaki kolaylaştırıcı türler.</span><span class="sxs-lookup"><span data-stu-id="dd124-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="dd124-125">Grafik ve Işleme</span><span class="sxs-lookup"><span data-stu-id="dd124-125">Graphics and Rendering</span></span>

<span data-ttu-id="dd124-126">WPF, yüksek kaliteli 2B grafikler için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="dd124-126">WPF includes support for high quality 2D graphics.</span></span> <span data-ttu-id="dd124-127">İşlevsellik, fırçalar, geometriler, görüntüler, şekiller ve dönüşümler içerir.</span><span class="sxs-lookup"><span data-stu-id="dd124-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="dd124-128">Daha fazla bilgi için bkz. [grafikler](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="dd124-129">Grafik öğelerinin işlenmesi sınıfı temel alır <xref:System.Windows.Media.Visual> .</span><span class="sxs-lookup"><span data-stu-id="dd124-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="dd124-130">Ekrandaki görsel nesnelerin yapısı, görsel ağaç tarafından açıklanmıştır.</span><span class="sxs-lookup"><span data-stu-id="dd124-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="dd124-131">Daha fazla bilgi için bkz. [WPF Grafik Işlemeye genel bakış](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2d-shapes"></a><span data-ttu-id="dd124-132">2B şekiller</span><span class="sxs-lookup"><span data-stu-id="dd124-132">2D Shapes</span></span>

<span data-ttu-id="dd124-133">WPF, aşağıdaki çizimin gösterdiği dikdörtgen ve elips gibi yaygın olarak kullanılan, vektör çizimli 2B şekillerin bir kitaplığını sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd124-133">WPF provides a library of commonly used, vector-drawn 2D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Üç nokta ve dikdörtgeni gösteren diyagram.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="dd124-135">Bu iç WPF şekilleri yalnızca şekil değildir: klavye ve fare girişi içeren en yaygın denetimlerden beklediğinizi birçok özelliği uygulayan programlanabilir öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="dd124-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="dd124-136">Aşağıdaki örnek, <xref:System.Windows.UIElement.MouseUp> bir öğesine tıklanarak oluşturulan olayın nasıl işleneceğini gösterir <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="dd124-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

```xaml
<Window
  xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
  xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
  x:Class="Window1" >
  <Ellipse Fill="LightBlue" MouseUp="ellipseButton_MouseUp" />
</Window>
```

```csharp
public partial class Window1  : Window
{
    void ellipseButton_MouseUp(object sender, MouseButtonEventArgs e)
    {
        MessageBox.Show("You clicked the ellipse!");
    }
}
```

```vb
Partial Public Class Window1
    Inherits Window
    Private Sub ellipseButton_MouseUp(ByVal sender As Object, ByVal e As MouseButtonEventArgs)
        MessageBox.Show("You clicked the ellipse!")
    End Sub
End Class
```

<span data-ttu-id="dd124-137">Aşağıdaki çizimde, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve arka plan kodu için çıkış gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd124-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

!["Elips tıkladınız!" ifadesini bildiren bir ileti kutusu](./media/index/messagebox-text-output.png)

<span data-ttu-id="dd124-139">Daha fazla bilgi için bkz. [WPF 'de şekillere ve temel çizime genel bakış](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="dd124-140">Bir tanıtıcı örnek için bkz. [Şekil öğeleri örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="dd124-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2d-geometries"></a><span data-ttu-id="dd124-141">2B geometriler</span><span class="sxs-lookup"><span data-stu-id="dd124-141">2D Geometries</span></span>

<span data-ttu-id="dd124-142">WPF 'in sağladığı 2B şekiller yeterli olmadığında, kendinizinkini oluşturmak için geometriler ve yollar için WPF desteği kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd124-142">When the 2D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="dd124-143">Aşağıdaki çizimde, bir çizim Fırçası olarak şekiller oluşturmak ve diğer WPF öğelerini kırpmak için geometriler nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd124-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Şekil oluşturmak için geometrilerin nasıl kullanılabileceğini gösteren ekran görüntüsü.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="dd124-145">Daha fazla bilgi için bkz. [geometriye genel bakış](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="dd124-146">Tanıtıcı bir örnek için bkz. [geometriler örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="dd124-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2d-effects"></a><span data-ttu-id="dd124-147">2B efektler</span><span class="sxs-lookup"><span data-stu-id="dd124-147">2D Effects</span></span>

<span data-ttu-id="dd124-148">WPF, çeşitli efektler oluşturmak için kullanabileceğiniz bir 2B sınıf kitaplığı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd124-148">WPF provides a library of 2D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="dd124-149">WPF 'in 2B işleme özelliği, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] degradeler, bit eşlemler, çizimler ve videolar içeren öğeleri boyama ve döndürme, ölçekleme ve eğriltme kullanarak bunları değiştirme olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd124-149">The 2D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="dd124-150">Aşağıdaki çizimde, WPF fırçalarını kullanarak elde edilebilecek birçok etkiye bir örnek verilmiştir.</span><span class="sxs-lookup"><span data-stu-id="dd124-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Farklı WPF fırçalarını ve boyama öğelerini gösteren çizim.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="dd124-152">Daha fazla bilgi için bkz. [WPF Fırçalarına Genel Bakış](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="dd124-153">Tanıtıcı bir örnek için bkz. [fırçalar örneği](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span><span class="sxs-lookup"><span data-stu-id="dd124-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3d-rendering"></a><span data-ttu-id="dd124-154">3B Işleme</span><span class="sxs-lookup"><span data-stu-id="dd124-154">3D Rendering</span></span>

<span data-ttu-id="dd124-155">WPF, daha heyecan verici düzen, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] ve veri görselleştirmesi oluşturabilmeniz IÇIN WPF 'de 2B grafik desteğiyle tümleştirilebilen bir dizi 3B işleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd124-155">WPF provides a set of 3D rendering capabilities that integrate with 2D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="dd124-156">Bu, tayfın bir ucunda, 2B görüntüleri aşağıdaki çizimin gösterdiği 3B şekillerin yüzeylerine göre işlemenizi sağlar.</span><span class="sxs-lookup"><span data-stu-id="dd124-156">At one end of the spectrum, WPF enables you to render 2D images onto the surfaces of 3D shapes, which the following illustration demonstrates.</span></span>

![Farklı dokularla 3B şekilleri gösteren örnek ekran görüntüsü.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="dd124-158">Daha fazla bilgi için bkz. [3B grafiklere genel bakış](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-158">For more information, see [3D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="dd124-159">Tanıtıcı bir örnek için bkz. [3B Solids örneği](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="dd124-159">For an introductory sample, see [3D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="dd124-160">Animasyon</span><span class="sxs-lookup"><span data-stu-id="dd124-160">Animation</span></span>

<span data-ttu-id="dd124-161">Denetimleri ve öğeleri büyütmek, sallama, döndürme ve belirme yapmak için animasyon kullanın; ve ilginç sayfa geçişleri ve daha fazlasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="dd124-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="dd124-162">WPF birçok özelliğe animasyon uygulamanızı sağladığından, yalnızca birçok WPF nesnesini hareketlendirmenize olanak tanıdığından, oluşturduğunuz özel nesnelere animasyon eklemek için WPF de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="dd124-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Animasyonlu küpün ekran görüntüsü.](./media/index/animate-custom-objects.png)

<span data-ttu-id="dd124-164">Daha fazla bilgi için bkz. [animasyon genel bakış](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="dd124-165">Bir tanıtıcı örnek için bkz. [animasyon örnek Galerisi](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="dd124-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="dd124-166">Medya</span><span class="sxs-lookup"><span data-stu-id="dd124-166">Media</span></span>

<span data-ttu-id="dd124-167">Görüntü, video ve ses, bilgi ve kullanıcı deneyimlerini vermenin zengin ortamlarıdır.</span><span class="sxs-lookup"><span data-stu-id="dd124-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="dd124-168">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="dd124-168">Images</span></span>

<span data-ttu-id="dd124-169">Simgeler, arka planlar ve hatta animasyonların parçaları dahil olmak üzere birçok uygulamanın temel bir parçası olan görüntüler.</span><span class="sxs-lookup"><span data-stu-id="dd124-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="dd124-170">Genellikle görüntüleri kullanmanız gerektiğinden, WPF bunlarla çeşitli yollarla çalışma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="dd124-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="dd124-171">Aşağıdaki çizimde bu yolların yalnızca biri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="dd124-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="dd124-172">![Stil örnek ekran görüntüsü](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="dd124-172">![Styling sample screenshot](../controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="dd124-173">Daha fazla bilgi için bkz. [Imaging 'e genel bakış](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="dd124-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="dd124-174">Video ve ses</span><span class="sxs-lookup"><span data-stu-id="dd124-174">Video and Audio</span></span>

<span data-ttu-id="dd124-175">WPF 'nin grafik özelliklerinin temel bir özelliği, video ve ses dahil olmak üzere multimedya ile çalışmaya yönelik yerel destek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="dd124-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="dd124-176">Aşağıdaki örnek, bir medya yürütücüsünün bir uygulamaya nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="dd124-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="dd124-177"><xref:System.Windows.Controls.MediaElement>hem video hem de ses oynamaya sahiptir ve özel Uıof 'ın kolay oluşturulmasına izin vermek için yeterince genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="dd124-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="dd124-178">Daha fazla bilgi için [Çoklu ortama genel bakış](multimedia-overview.md)konusuna bakın.</span><span class="sxs-lookup"><span data-stu-id="dd124-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="dd124-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dd124-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="dd124-180">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="dd124-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="dd124-181">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="dd124-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="dd124-182">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd124-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="dd124-183">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="dd124-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="dd124-184">Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="dd124-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="dd124-185">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd124-185">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="dd124-186">Multimedyaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="dd124-186">Multimedia Overview</span></span>](multimedia-overview.md)
