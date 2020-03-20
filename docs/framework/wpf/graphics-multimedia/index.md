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
ms.openlocfilehash: 56a69c10a420e399478a0d617d30380ff5217e9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186725"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="30bb5-102">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="30bb5-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="30bb5-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]multimedya, vektör grafikleri, animasyon ve içerik kompozisyonu için destek sağlayarak geliştiricilerin ilginç kullanıcı arabirimleri ve içerik oluşturmalarını kolaylaştırır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="30bb5-104">Visual Studio'yu kullanarak vektör grafikleri veya karmaşık animasyonlar oluşturabilir ve ortamı uygulamalarınız için entegre edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30bb5-104">Using Visual Studio, you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="30bb5-105">Bu konu, uygulamalarınıza grafik, geçiş [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]efektleri, ses ve video eklemenize olanak tanıyan grafik, animasyon ve medya özelliklerini tanır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="30bb5-106">Bir Windows hizmetinde WPF türlerinin kullanılması nın önerilmesi kuvvetle yapılır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="30bb5-107">Bir Windows hizmetinde WPF türlerini kullanmaya çalışırsanız, hizmet beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="30bb5-108">WPF 4'te Grafik ve Multimedya ile Yenilikler</span><span class="sxs-lookup"><span data-stu-id="30bb5-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="30bb5-109">Grafik ve animasyonlarla ilgili çeşitli değişiklikler yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="30bb5-110">Düzen Yuvarlama</span><span class="sxs-lookup"><span data-stu-id="30bb5-110">Layout Rounding</span></span>

  <span data-ttu-id="30bb5-111">Bir nesne kenarı bir piksel aygıtının ortasına düştüğünde, DPI'dan bağımsız grafik sistemi bulanık veya yarı saydam kenarlar gibi işleme yapıları oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="30bb5-112">WPF'nin önceki sürümlerinde bu servis talebinin ele alınaması için piksel tutturulması da yer aldı.</span><span class="sxs-lookup"><span data-stu-id="30bb5-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="30bb5-113">Silverlight 2, kenarların tüm piksel sınırlarına düşmesi için öğeleri taşımanın başka bir yolu olan düzen yuvarlama ile tanıtıldı.</span><span class="sxs-lookup"><span data-stu-id="30bb5-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="30bb5-114">WPF artık <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> ekli özellik ile düzen <xref:System.Windows.FrameworkElement>yuvarlama destekler.</span><span class="sxs-lookup"><span data-stu-id="30bb5-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="30bb5-115">Önbelleğe Alınmış Kompozisyon</span><span class="sxs-lookup"><span data-stu-id="30bb5-115">Cached Composition</span></span>

  <span data-ttu-id="30bb5-116">Yeni <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıfları kullanarak, görsel ağacın karmaşık bir bölümünü bit eşlemi olarak önbelleğe alabilir ve işleme süresini büyük ölçüde artırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30bb5-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="30bb5-117">Bit eşlemi fare tıklamaları gibi kullanıcı girişine yanıt vermeye devam eder ve bunu herhangi bir fırça gibi diğer öğelere boyayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30bb5-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="30bb5-118">Pixel Shader 3 Desteği</span><span class="sxs-lookup"><span data-stu-id="30bb5-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="30bb5-119">WPF 4, Pixel Shader (PS) sürüm 3.0 kullanarak uygulamaların efekt yazmasına izin vererek WPF 3.5 SP1'de tanıtılan <xref:System.Windows.Media.Effects.ShaderEffect> desteğin üzerine kuruludur.</span><span class="sxs-lookup"><span data-stu-id="30bb5-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="30bb5-120">PS 3.0 shader modeli, desteklenen donanım üzerinde daha fazla etki sağlayan PS 2.0'dan daha gelişmiştir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="30bb5-121">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="30bb5-121">Easing Functions</span></span>

  <span data-ttu-id="30bb5-122">Animasyonları kolaylaştırma işlevleriyle büyütebilirsiniz, bu da animasyonların davranışı üzerinde ek denetim sağlar.</span><span class="sxs-lookup"><span data-stu-id="30bb5-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="30bb5-123">Örneğin, animasyona yaylı bir davranış vermek için animasyona bir <xref:System.Windows.Media.Animation.ElasticEase> animasyon uygulayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30bb5-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="30bb5-124">Daha fazla bilgi için ad <xref:System.Windows.Media.Animation> alanındaki kolaylaştırma türlerine bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="30bb5-125">Grafik ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="30bb5-125">Graphics and Rendering</span></span>

<span data-ttu-id="30bb5-126">WPF, yüksek kaliteli 2-B grafikler için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="30bb5-127">İşlevsellik fırçalar, geometriler, görüntüler, şekiller ve dönüşümler içerir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="30bb5-128">Daha fazla bilgi için [Bkz. Grafik.](graphics.md)</span><span class="sxs-lookup"><span data-stu-id="30bb5-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="30bb5-129">Grafik öğelerinin işlenmesi sınıfa <xref:System.Windows.Media.Visual> dayanır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="30bb5-130">Ekrandaki görsel nesnelerin yapısı görsel ağaç tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="30bb5-131">Daha fazla bilgi için [WPF Grafik Oluşturma Genel Bakış'a](wpf-graphics-rendering-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="30bb5-132">2-B Şekiller</span><span class="sxs-lookup"><span data-stu-id="30bb5-132">2-D Shapes</span></span>

<span data-ttu-id="30bb5-133">WPF, aşağıdaki resimde gösterildiği gibi dikdörtgenler ve elipsler gibi yaygın olarak kullanılan vektör çizimli 2-B şekillerden oluşan bir kitaplık sağlar.</span><span class="sxs-lookup"><span data-stu-id="30bb5-133">WPF provides a library of commonly used, vector-drawn 2-D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Elipsleri ve dikdörtgenleri gösteren diyagram.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="30bb5-135">Bu içsel WPF şekilleri sadece şekiller değildir: klavye ve fare girişi içeren en yaygın denetimlerden beklediğiniz özelliklerin çoğunu uygulayan programlanabilir öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-135">These intrinsic WPF shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="30bb5-136">Aşağıdaki örnek, bir <xref:System.Windows.UIElement.MouseUp> <xref:System.Windows.Shapes.Ellipse> öğeyi tıklatarak yükseltilen olayın nasıl işleyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="30bb5-137">Aşağıdaki resimde önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve kod arkası çıktısı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

!["Elipsi tıklattın!" yazan bir mesaj kutusu](./media/index/messagebox-text-output.png)

<span data-ttu-id="30bb5-139">Daha fazla bilgi için [WPF'ye Genel Bakış'ta Şekiller ve Temel Çizim'e](shapes-and-basic-drawing-in-wpf-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="30bb5-140">Bir tanıtım örneği için [Şekil Elemanları Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-140">For an introductory sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="30bb5-141">2-B Geometriler</span><span class="sxs-lookup"><span data-stu-id="30bb5-141">2-D Geometries</span></span>

<span data-ttu-id="30bb5-142">WPF'nin sağladığı 2-B şekiller yeterli olmadığında, kendi şekillerinizi oluşturmak için geometriler ve yollar için WPF desteğini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30bb5-142">When the 2-D shapes that WPF provides are not sufficient, you can use WPF support for geometries and paths to create your own.</span></span> <span data-ttu-id="30bb5-143">Aşağıdaki resimde, çizim fırçası olarak şekiller oluşturmak ve diğer WPF öğelerini kesmek için geometrileri nasıl kullanabileceğiniz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other WPF elements.</span></span>

![Şekiller oluşturmak için geometrileri nasıl kullanabileceğinizi gösteren ekran görüntüsü.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="30bb5-145">Daha fazla bilgi için [Geometriye Genel Bakış'a](geometry-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="30bb5-146">Bir tanıtım örneği için [Geometriler Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-146">For an introductory sample, see [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="30bb5-147">2-B Etkileri</span><span class="sxs-lookup"><span data-stu-id="30bb5-147">2-D Effects</span></span>

<span data-ttu-id="30bb5-148">WPF, çeşitli efektler oluşturmak için kullanabileceğiniz 2-B sınıflardan oluşan bir kitaplık sağlar.</span><span class="sxs-lookup"><span data-stu-id="30bb5-148">WPF provides a library of 2-D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="30bb5-149">WPF'nin 2-B işleme özelliği, degradelere, bit eşlemlere, çizimlere ve videolara sahip öğeleri boyama [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] olanağı sağlar; ve döndürme, ölçekleme ve eğrilme kullanarak onları işlemek için.</span><span class="sxs-lookup"><span data-stu-id="30bb5-149">The 2-D rendering capability of WPF provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="30bb5-150">Aşağıdaki resimde WPF fırçaları kullanarak elde edebilirsiniz birçok etkileri bir örnek verir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-150">The following illustration gives an example of the many effects you can achieve by using WPF brushes.</span></span>

![Farklı WPF fırçalarını ve boya elemanlarını gösteren çizim.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="30bb5-152">Daha fazla bilgi için [WPF Fırçalar Genel Bakış'a](wpf-brushes-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="30bb5-153">Bir tanıtım örneği için [Fırçalar Örneği'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-153">For an introductory sample, see [Brushes Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Brushes).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="30bb5-154">3-B Rendering</span><span class="sxs-lookup"><span data-stu-id="30bb5-154">3-D Rendering</span></span>

<span data-ttu-id="30bb5-155">WPF, daha heyecan verici düzen [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ve veri görselleştirmesi oluşturmanız için WPF'de 2-B grafik desteğiyle entegre olan bir dizi 3-B görüntüleme özelliği sağlar.</span><span class="sxs-lookup"><span data-stu-id="30bb5-155">WPF provides a set of 3-D rendering capabilities that integrate with 2-D graphics support in WPF in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="30bb5-156">Spektrumun bir ucunda, WPF 2-B görüntüleri aşağıdaki resimde gösterdiği 3-B şekillerin yüzeylerine oluşturmanızı sağlar.</span><span class="sxs-lookup"><span data-stu-id="30bb5-156">At one end of the spectrum, WPF enables you to render 2-D images onto the surfaces of 3-D shapes, which the following illustration demonstrates.</span></span>

![Farklı dokulara sahip 3 B şekilleri gösteren bir örneğin ekran görüntüsü.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="30bb5-158">Daha fazla bilgi için [3-B Grafik Genel Bakışı'na](3-d-graphics-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="30bb5-159">Bir tanıtım örneği için [3-B Katı Numunesi'ne](https://go.microsoft.com/fwlink/?LinkID=159964)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="30bb5-160">Animasyon</span><span class="sxs-lookup"><span data-stu-id="30bb5-160">Animation</span></span>

<span data-ttu-id="30bb5-161">Denetimlerin ve öğelerin büyümesini, sallanmasını, dönmesini ve solmasını sağlamak için animasyonu kullanın; ve ilginç sayfa geçişleri oluşturmak ve daha fazlası.</span><span class="sxs-lookup"><span data-stu-id="30bb5-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="30bb5-162">WPF çoğu özelliği animasyona reanimasyon alabilmenizi sağladığından, yalnızca çoğu WPF nesnesini canlandırmakla kullanabilirsiniz, ayrıca oluşturduğunuz özel nesneleri canlandırmak için WPF'yi de kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="30bb5-162">Because WPF enables you to animate most properties, not only can you animate most WPF objects, you can also use WPF to animate custom objects that you create.</span></span>

![Animasyonlu küpün ekran görüntüsü.](./media/index/animate-custom-objects.png)

<span data-ttu-id="30bb5-164">Daha fazla bilgi için [Animasyona Genel Bakış'a](animation-overview.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="30bb5-165">Tanıtım örneği için [Animasyon Örnek Galerisi'ne](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples)bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-165">For an introductory sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="30bb5-166">Medya</span><span class="sxs-lookup"><span data-stu-id="30bb5-166">Media</span></span>

<span data-ttu-id="30bb5-167">Görüntüler, video ve ses, bilgi ve kullanıcı deneyimlerini aktarmanın medya açısından zengin yollarıdır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="30bb5-168">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="30bb5-168">Images</span></span>

<span data-ttu-id="30bb5-169">Simgeleri, arka planlar ve hatta animasyonların parçalarını içeren görüntüler çoğu uygulamanın temel parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="30bb5-170">Sık sık görüntüleri kullanmanız gerektiğinden, WPF onlarla çeşitli şekillerde çalışma yeteneğini ortaya çıkarır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-170">Because you frequently need to use images, WPF exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="30bb5-171">Aşağıdaki resimde bu yollardan yalnızca biri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="30bb5-172">![Stil örnek ekran görüntüsü](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="30bb5-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="30bb5-173">Daha fazla bilgi için [Görüntülemegenel bakış](imaging-overview.md)bilgisine bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="30bb5-174">Video ve Ses</span><span class="sxs-lookup"><span data-stu-id="30bb5-174">Video and Audio</span></span>

<span data-ttu-id="30bb5-175">WPF grafik yetenekleri bir temel özelliği video ve ses içeren multimedya ile çalışmak için yerel destek sağlamaktır.</span><span class="sxs-lookup"><span data-stu-id="30bb5-175">A core feature of the graphics capabilities of WPF is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="30bb5-176">Aşağıdaki örnek, bir ortam oynatıcısının uygulamaya nasıl yerleştirilebildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="30bb5-177"><xref:System.Windows.Controls.MediaElement>hem video hem de ses oynatma yeteneğine sahiptir ve özel Kullanıcı II'lerin kolay oluşturulmasına izin verecek kadar genişletilebilir.</span><span class="sxs-lookup"><span data-stu-id="30bb5-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom UIs.</span></span>

<span data-ttu-id="30bb5-178">Daha fazla bilgi için [Multimedyagenel bakış](multimedia-overview.md)ına bakın.</span><span class="sxs-lookup"><span data-stu-id="30bb5-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="30bb5-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30bb5-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="30bb5-180">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="30bb5-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="30bb5-181">WPF Genel Bakışı İçinde Şekiller ve Temel Çizimler</span><span class="sxs-lookup"><span data-stu-id="30bb5-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="30bb5-182">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30bb5-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="30bb5-183">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="30bb5-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="30bb5-184">Animasyon ve Zamanlama ile İlgili Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="30bb5-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="30bb5-185">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30bb5-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="30bb5-186">Multimedyaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="30bb5-186">Multimedia Overview</span></span>](multimedia-overview.md)
