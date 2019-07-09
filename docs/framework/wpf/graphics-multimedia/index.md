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
ms.openlocfilehash: a770bcbbc8ac553c55e9dda5097abec8790182e5
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663731"
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="b1c28-102">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="b1c28-102">Graphics and Multimedia</span></span>

<a name="introduction"></a>
<span data-ttu-id="b1c28-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] multimedya, vektör grafikleri, animasyon ve ilgi çekici kullanıcı arabirimleri ve içerik oluşturmak geliştiriciler için kolaylaştıran, içerik oluşturma için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1c28-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="b1c28-104">Kullanarak [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vektör grafik veya karmaşık animasyonları oluşturun ve medya uygulamalarınızla tümleştirin.</span><span class="sxs-lookup"><span data-stu-id="b1c28-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>

<span data-ttu-id="b1c28-105">Bu konuda, grafik, animasyon ve medya özelliklerini tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], grafik, geçiş efektleri, ses ve video uygulamalarınıza ekleyin etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="b1c28-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>

> [!NOTE]
> <span data-ttu-id="b1c28-106">WPF türlerini kullanarak bir Windows hizmetinde kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="b1c28-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="b1c28-107">Bir Windows hizmetinde WPF türleri kullanmayı denerseniz, hizmetin beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="b1c28-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>

<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>

## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="b1c28-108">Grafikler ve multimedya WPF 4 ile yenilikler</span><span class="sxs-lookup"><span data-stu-id="b1c28-108">What's New with Graphics and Multimedia in WPF 4</span></span>

<span data-ttu-id="b1c28-109">Grafikler ve animasyon ilgili birkaç değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b1c28-109">Several changes have been made related to graphics and animations.</span></span>

- <span data-ttu-id="b1c28-110">Düzen yuvarlama</span><span class="sxs-lookup"><span data-stu-id="b1c28-110">Layout Rounding</span></span>

  <span data-ttu-id="b1c28-111">Bir nesnenin kenar ortasında bir pixel cihazda düştüğünde DPI bağımsız grafik sistemi bulanık veya yarı saydam kenarları gibi işleme yapılarını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1c28-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="b1c28-112">WPF önceki sürümleri, bu durumda işlemeye yardımcı olmak için piksel yaslamayı dahil.</span><span class="sxs-lookup"><span data-stu-id="b1c28-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="b1c28-113">Silverlight 2 Düzen yuvarlama, tüm piksel sınırlardaki kenarları kalan öğeleri taşımak, başka bir yolu olan sunulmuştur.</span><span class="sxs-lookup"><span data-stu-id="b1c28-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="b1c28-114">WPF düzen ile yuvarlama artık destekliyor <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> üzerinde ekli özellik <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="b1c28-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>

- <span data-ttu-id="b1c28-115">Önbelleğe alınan oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1c28-115">Cached Composition</span></span>

  <span data-ttu-id="b1c28-116">Yeni kullanarak <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıfları, bit eşlem olarak görsel ağacı karmaşık bir kısmını önbelleğe ve işleme süresini önemli ölçüde geliştirmek.</span><span class="sxs-lookup"><span data-stu-id="b1c28-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="b1c28-117">Bit eşlem fare tıklama gibi kullanıcı girişine yanıt olarak kalır ve herhangi bir fırça gibi diğer öğeler üzerine boyama.</span><span class="sxs-lookup"><span data-stu-id="b1c28-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>

- <span data-ttu-id="b1c28-118">Piksel gölgelendirici 3 desteği</span><span class="sxs-lookup"><span data-stu-id="b1c28-118">Pixel Shader 3 Support</span></span>

  <span data-ttu-id="b1c28-119">WPF 4 derlemeleri üst kısmındaki <xref:System.Windows.Media.Effects.ShaderEffect> etkileri piksel gölgelendiricisi (PS) sürüm 3.0 kullanarak yazmak uygulamaları sağlayarak WPF 3.5 SP1'de sunulan destek.</span><span class="sxs-lookup"><span data-stu-id="b1c28-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="b1c28-120">PS 3.0 gölgelendirici modeli desteklenen donanım üzerinde daha fazla efekte sağlayan PS 2.0 daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="b1c28-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>

- <span data-ttu-id="b1c28-121">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="b1c28-121">Easing Functions</span></span>

  <span data-ttu-id="b1c28-122">Animasyon davranışları üzerinde ek denetim size kolaylaştırıcı işlevler animasyonlarla geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b1c28-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="b1c28-123">Örneğin, geçerli bir <xref:System.Windows.Media.Animation.ElasticEase> animasyon esnek bir davranış sağlamak için bir animasyon için.</span><span class="sxs-lookup"><span data-stu-id="b1c28-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="b1c28-124">Kolaylaştırıcı türlerinde daha fazla bilgi için bkz. <xref:System.Windows.Media.Animation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="b1c28-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>

<a name="graphics_and_rendering"></a>

## <a name="graphics-and-rendering"></a><span data-ttu-id="b1c28-125">Grafik ve oluşturma</span><span class="sxs-lookup"><span data-stu-id="b1c28-125">Graphics and Rendering</span></span>

<span data-ttu-id="b1c28-126">WPF, yüksek kaliteli 2B grafikler için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="b1c28-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="b1c28-127">Fırçalar, geometri, resimler, şekiller ve dönüşümler işlevleri içerir.</span><span class="sxs-lookup"><span data-stu-id="b1c28-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="b1c28-128">Daha fazla bilgi için [grafik](graphics.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-128">For more information, see [Graphics](graphics.md).</span></span> <span data-ttu-id="b1c28-129">Grafik öğelerin işlenmesi dayanır <xref:System.Windows.Media.Visual> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="b1c28-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="b1c28-130">Görsel nesneler ekranında yapısını görsel ağacını tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="b1c28-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="b1c28-131">Daha fazla bilgi için [WPF Grafik işlemeye genel bakış](wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-131">For more information, see [WPF Graphics Rendering Overview](wpf-graphics-rendering-overview.md).</span></span>

### <a name="2-d-shapes"></a><span data-ttu-id="b1c28-132">2B şekiller</span><span class="sxs-lookup"><span data-stu-id="b1c28-132">2-D Shapes</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="b1c28-133">yaygın olarak kullanılan, vektör çizimli 2B şekiller, dikdörtgenler ve elipsler aşağıdaki çizimin gösterdiği gibi bir kitaplık sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1c28-133">provides a library of commonly used, vector-drawn 2-D shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>

![Diyagram gösteren elips ve dikdörtgen.](./media/index/two-deminsional-shapes-ellipses-rectangles.png)

<span data-ttu-id="b1c28-135">Bu iç [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] şekilleri yalnızca şekil değil: Bunlar birçok klavye ve fare girişi içeren, en yaygın denetimlerden beklediğiniz özelliği uygulayan programlanabilir öğeleridir.</span><span class="sxs-lookup"><span data-stu-id="b1c28-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="b1c28-136">Aşağıdaki örnek nasıl işleneceğini gösterir <xref:System.Windows.UIElement.MouseUp> tıklayarak harekete geçirilen olay bir <xref:System.Windows.Shapes.Ellipse> öğesi.</span><span class="sxs-lookup"><span data-stu-id="b1c28-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>

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

<span data-ttu-id="b1c28-137">Önceki çıktı aşağıda gösterilmiştir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] işaretleme ve arka plan kod.</span><span class="sxs-lookup"><span data-stu-id="b1c28-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>

!["Elips tıkladığınız!" belirten bir ileti kutusu](./media/index/messagebox-text-output.png)

<span data-ttu-id="b1c28-139">Daha fazla bilgi için [şekiller ve temel çizimlere WPF genel bakışında](shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-139">For more information, see [Shapes and Basic Drawing in WPF Overview](shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="b1c28-140">Tanıtıcı bir örnek için bkz. [şekil öğeleri örneği](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="b1c28-140">For an introductory sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>

### <a name="2-d-geometries"></a><span data-ttu-id="b1c28-141">2B geometri</span><span class="sxs-lookup"><span data-stu-id="b1c28-141">2-D Geometries</span></span>

<span data-ttu-id="b1c28-142">Ne zaman 2B şekiller, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar kullanabileceğiniz yeterli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geometrileri ve kendi yolları için destek.</span><span class="sxs-lookup"><span data-stu-id="b1c28-142">When the 2-D shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="b1c28-143">Aşağıdaki çizimde, çizim Fırçası gibi şekiller, oluşturmak ve diğeri küçük resim için geometri nasıl kullanabileceğinizi gösterir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri.</span><span class="sxs-lookup"><span data-stu-id="b1c28-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>

![Şekiller oluşturmaya geometriler nasıl kullanabileceğinizi gösteren ekran görüntüsü.](./media/index/use-geometries-create-shapes.png)

<span data-ttu-id="b1c28-145">Daha fazla bilgi için [geometrisi](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-145">For more information, see [Geometry Overview](geometry-overview.md).</span></span> <span data-ttu-id="b1c28-146">Tanıtıcı bir örnek için bkz. [geometri örneği](https://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="b1c28-146">For an introductory sample, see [Geometries Sample](https://go.microsoft.com/fwlink/?LinkID=159989).</span></span>

### <a name="2-d-effects"></a><span data-ttu-id="b1c28-147">2B efektler</span><span class="sxs-lookup"><span data-stu-id="b1c28-147">2-D Effects</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="b1c28-148">2B sınıflarının çeşitli efektleri oluşturmak için kullanabileceğiniz bir kitaplık sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1c28-148">provides a library of 2-D classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="b1c28-149">2B işleme yeteneğini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] boyama olanak tanıyor [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gradyan, bit eşlemler, çizimler ve videoları; olan öğeler ve döndürme, kullanarak işlemek için ölçeklendirme ve eğriltme.</span><span class="sxs-lookup"><span data-stu-id="b1c28-149">The 2-D rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="b1c28-150">Aşağıdaki resimde bir örnek kullanarak elde edebileceğiniz birçok etkileri verir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Fırçalar.</span><span class="sxs-lookup"><span data-stu-id="b1c28-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>

![Farklı WPF fırçalarına ve bir boyama öğeleri gösteren şekil.](./media/index/brushes-paint-elements.png)

<span data-ttu-id="b1c28-152">Daha fazla bilgi için [WPF fırçalarına genel bakış](wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-152">For more information, see [WPF Brushes Overview](wpf-brushes-overview.md).</span></span> <span data-ttu-id="b1c28-153">Tanıtıcı bir örnek için bkz. [Fırçalar örnek](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="b1c28-153">For an introductory sample, see [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>

<a name="rendering"></a>

## <a name="3-d-rendering"></a><span data-ttu-id="b1c28-154">3B işleme</span><span class="sxs-lookup"><span data-stu-id="b1c28-154">3-D Rendering</span></span>

[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] <span data-ttu-id="b1c28-155">2B grafikler desteği tümleştirin 3B işleme özellikleri sunmaktadır [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] daha heyecan verici düzen oluşturmak için sırayla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ve veri görselleştirmesi.</span><span class="sxs-lookup"><span data-stu-id="b1c28-155">provides a set of 3-D rendering capabilities that integrate with 2-D graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="b1c28-156">Spektrumun bir sonunda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] 2B görüntülerin aşağıdaki çizimde gösterilmiştir 3B şekillerden yüzeyleriyle sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1c28-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render 2-D images onto the surfaces of 3-D shapes, which the following illustration demonstrates.</span></span>

![Farklı dokular ile 3B şekillerden gösteren örnek bir ekran görüntüsü.](./media/index/visual-three-dimensional-shape.png)

<span data-ttu-id="b1c28-158">Daha fazla bilgi için [3B Grafiklere Genel Bakış](3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-158">For more information, see [3-D Graphics Overview](3-d-graphics-overview.md).</span></span> <span data-ttu-id="b1c28-159">Tanıtıcı bir örnek için bkz. [3-b düz çizgi örneği](https://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="b1c28-159">For an introductory sample, see [3-D Solids Sample](https://go.microsoft.com/fwlink/?LinkID=159964).</span></span>

<a name="animation"></a>

## <a name="animation"></a><span data-ttu-id="b1c28-160">Animasyon</span><span class="sxs-lookup"><span data-stu-id="b1c28-160">Animation</span></span>

<span data-ttu-id="b1c28-161">Animasyon denetimleri ve büyütün, sallayın, çalıştırın ve Soluklaştır öğeleri yapmak için kullanın. ve ilgi çekici sayfa geçişleri ve daha fazlasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="b1c28-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="b1c28-162">Çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] etkinleştirir, özelliklerin çoğu, yalnızca animasyon uygulamak için birçok animasyon [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nesnelerini de kullanabilirsiniz [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturduğunuz özel nesneleri animasyon uygulamak için.</span><span class="sxs-lookup"><span data-stu-id="b1c28-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>

![Animasyonlu bir küpün ekran görüntüsü.](./media/index/animate-custom-objects.png)

<span data-ttu-id="b1c28-164">Daha fazla bilgi için [animasyona genel bakış](animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-164">For more information, see [Animation Overview](animation-overview.md).</span></span> <span data-ttu-id="b1c28-165">Tanıtıcı bir örnek için bkz. [animasyon örnek Galerisi](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="b1c28-165">For an introductory sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>

<a name="media"></a>

## <a name="media"></a><span data-ttu-id="b1c28-166">Medya</span><span class="sxs-lookup"><span data-stu-id="b1c28-166">Media</span></span>

<span data-ttu-id="b1c28-167">Görüntü, video ve ses bilgileri ve kullanıcı deneyimlerini yaygınlaşmıştır, zengin medya yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="b1c28-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>

### <a name="images"></a><span data-ttu-id="b1c28-168">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="b1c28-168">Images</span></span>

<span data-ttu-id="b1c28-169">Görüntüler, simgeler, arka plan ve hatta animasyonları parçalarını içeren çoğu uygulamalar çekirdek parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="b1c28-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="b1c28-170">Sık görüntüleri kullanmanız gerekir çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çeşitli yollarla onlarla çalışma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="b1c28-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="b1c28-171">Bu yollardan yalnızca biri aşağıda gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="b1c28-171">The following illustration shows just one of those ways.</span></span>

<span data-ttu-id="b1c28-172">![Stil örnek ekran](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="b1c28-172">![Styling sample screenshot](../controls/./media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>

<span data-ttu-id="b1c28-173">Daha fazla bilgi için [Imaging genel bakış](imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-173">For more information, see [Imaging Overview](imaging-overview.md).</span></span>

### <a name="video-and-audio"></a><span data-ttu-id="b1c28-174">Video ve ses</span><span class="sxs-lookup"><span data-stu-id="b1c28-174">Video and Audio</span></span>

<span data-ttu-id="b1c28-175">Çekirdek özelliği, grafik yeteneklerini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] video ve ses içeren çoklu ortam ile çalışmak için yerel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="b1c28-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="b1c28-176">Aşağıdaki örnek bir medya yürütücüsü bir uygulamaya nasıl ekleneceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="b1c28-176">The following example shows how to insert a media player into an application.</span></span>

```xaml
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />
```

<span data-ttu-id="b1c28-177"><xref:System.Windows.Controls.MediaElement> video ve ses çalabilir ve özel bir kolayca oluşturulmasını izin vermek için Genişletilebilir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="b1c28-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span></span>

<span data-ttu-id="b1c28-178">Daha fazla bilgi için [multimedya genel bakış](multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b1c28-178">For more information, see the [Multimedia Overview](multimedia-overview.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b1c28-179">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b1c28-179">See also</span></span>

- <xref:System.Windows.Media>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Media3D>
- [<span data-ttu-id="b1c28-180">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="b1c28-180">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="b1c28-181">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1c28-181">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="b1c28-182">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1c28-182">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="b1c28-183">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="b1c28-183">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
- [<span data-ttu-id="b1c28-184">Animasyon ve zamanlama ile ilgili nasıl yapılır konuları</span><span class="sxs-lookup"><span data-stu-id="b1c28-184">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="b1c28-185">3B Grafiklere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1c28-185">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="b1c28-186">Multimedyaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="b1c28-186">Multimedia Overview</span></span>](multimedia-overview.md)
