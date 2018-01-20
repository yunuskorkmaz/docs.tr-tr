---
title: Grafikler ve Multimedya
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
- media [WPF], features
- video effects [WPF]
- sound effects [WPF]
- animation [WPF], features
- graphics features [WPF]
- transition effects [WPF]
ms.assetid: 1817d9dc-3d6c-46cb-afc8-63b0bae35e37
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 013ae46e2d90a9eda42d33e95e590812489fa04b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="graphics-and-multimedia"></a><span data-ttu-id="da0d2-102">Grafikler ve Multimedya</span><span class="sxs-lookup"><span data-stu-id="da0d2-102">Graphics and Multimedia</span></span>
<a name="introduction"></a>
<span data-ttu-id="da0d2-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]multimedya, vektör grafikleri, animasyon ve ilginç kullanıcı arabirimleri ve içerik oluşturmada geliştiricilere kolaylaşır içerik oluşturma için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="da0d2-103">[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] provides support for multimedia, vector graphics, animation, and content composition, making it easy for developers to build interesting user interfaces and content.</span></span> <span data-ttu-id="da0d2-104">Kullanarak [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], vektör grafikleri veya karmaşık bir animasyon oluşturabilir ve ortam uygulamalarınıza tümleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0d2-104">Using [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], you can create vector graphics or complex animations and integrate media into your applications.</span></span>  
  
 <span data-ttu-id="da0d2-105">Bu konu, grafik, animasyon ve ortam özelliklerini tanıtır [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], grafik, geçiş efektleri, ses ve video uygulamalarınıza eklemek etkinleştirin.</span><span class="sxs-lookup"><span data-stu-id="da0d2-105">This topic introduces the graphics, animation, and media features of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], which enable you to add graphics, transition effects, sound, and video to your applications.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da0d2-106">Bir Windows hizmetinde WPF türlerini kullanarak kesinlikle önerilmez.</span><span class="sxs-lookup"><span data-stu-id="da0d2-106">Using WPF types in a Windows service is strongly discouraged.</span></span> <span data-ttu-id="da0d2-107">Bir Windows hizmetinde WPF türleri kullanmayı denerseniz, hizmet beklendiği gibi çalışmayabilir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-107">If you attempt to use WPF types in a Windows service, the service may not work as expected.</span></span>   
  
<a name="whats_new_with_graphics_and_multimedia_in_wpf_4"></a>   
## <a name="whats-new-with-graphics-and-multimedia-in-wpf-4"></a><span data-ttu-id="da0d2-108">Grafiklerle ve WPF 4 multimedya yenilikler</span><span class="sxs-lookup"><span data-stu-id="da0d2-108">What's New with Graphics and Multimedia in WPF 4</span></span>  
 <span data-ttu-id="da0d2-109">Grafikler ve animasyon ilgili birkaç değişiklik yapılmıştır.</span><span class="sxs-lookup"><span data-stu-id="da0d2-109">Several changes have been made related to graphics and animations.</span></span>  
  
-   <span data-ttu-id="da0d2-110">Düzen yuvarlama</span><span class="sxs-lookup"><span data-stu-id="da0d2-110">Layout Rounding</span></span>  
  
     <span data-ttu-id="da0d2-111">DPI bağımsız grafik sistemi nesnenin bir kenarı piksel aygıtının ortasında düştüğünde bulanık veya yarı saydam kenarlar gibi işleme yapılarını oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0d2-111">When an object edge falls in the middle of a pixel device, the DPI-independent graphics system can create rendering artifacts, such as blurry or semi-transparent edges.</span></span> <span data-ttu-id="da0d2-112">WPF önceki sürümleri, bu durumda işlemeye yardımcı olmak için piksel tutturma dahil.</span><span class="sxs-lookup"><span data-stu-id="da0d2-112">Previous versions of WPF included pixel snapping to help handle this case.</span></span> <span data-ttu-id="da0d2-113">Silverlight 2 düzeni yuvarlama, böylece Kenarları piksel sınırlarının tamamına kalan öğeleri taşımak için başka bir yol olduğu sunmuştur.</span><span class="sxs-lookup"><span data-stu-id="da0d2-113">Silverlight 2 introduced layout rounding, which is another way to move elements so that edges fall on whole pixel boundaries.</span></span> <span data-ttu-id="da0d2-114">WPF ile yuvarlama düzeni artık destekliyor <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> üzerinde ekli özellik <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="da0d2-114">WPF now supports layout rounding with the <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> attached property on <xref:System.Windows.FrameworkElement>.</span></span>  
  
-   <span data-ttu-id="da0d2-115">Önbelleğe alınan oluşturma</span><span class="sxs-lookup"><span data-stu-id="da0d2-115">Cached Composition</span></span>  
  
     <span data-ttu-id="da0d2-116">Yeni kullanarak <xref:System.Windows.Media.BitmapCache> ve <xref:System.Windows.Media.BitmapCacheBrush> sınıfları, bit eşlem olarak görsel ağaç karmaşık bir kısmını önbelleğe ve işleme süresini önemli ölçüde artırmak.</span><span class="sxs-lookup"><span data-stu-id="da0d2-116">By using the new <xref:System.Windows.Media.BitmapCache> and <xref:System.Windows.Media.BitmapCacheBrush> classes, you can cache a complex part of the visual tree as a bitmap and greatly improve rendering time.</span></span> <span data-ttu-id="da0d2-117">Bit eşlem fare tıklamaları gibi kullanıcı girişine yanıt vermeyi kalır ve herhangi bir fırça gibi diğer öğeler üzerine boyamak.</span><span class="sxs-lookup"><span data-stu-id="da0d2-117">The bitmap remains responsive to user input, such as mouse clicks, and you can paint it onto other elements just like any brush.</span></span>  
  
-   <span data-ttu-id="da0d2-118">Piksel gölgelendirici 3 desteği</span><span class="sxs-lookup"><span data-stu-id="da0d2-118">Pixel Shader 3 Support</span></span>  
  
     <span data-ttu-id="da0d2-119">WPF 4 derlemeler üstünde <xref:System.Windows.Media.Effects.ShaderEffect> piksel gölgelendirici (PS) sürüm 3.0 kullanarak etkileri yazmak uygulamaları vererek WPF 3.5 SP1'de sunulan destek.</span><span class="sxs-lookup"><span data-stu-id="da0d2-119">WPF 4 builds on top of the <xref:System.Windows.Media.Effects.ShaderEffect> support introduced in WPF 3.5 SP1 by allowing applications to write effects by using Pixel Shader (PS) version 3.0.</span></span> <span data-ttu-id="da0d2-120">PS 3.0 gölgelendirici modeli desteklenen donanım daha da fazla etkileri izin veren PS 2.0 daha karmaşıktır.</span><span class="sxs-lookup"><span data-stu-id="da0d2-120">The PS 3.0 shader model is more sophisticated than PS 2.0, which allows for even more effects on supported hardware.</span></span>  
  
-   <span data-ttu-id="da0d2-121">Kolaylaştırıcı İşlevler</span><span class="sxs-lookup"><span data-stu-id="da0d2-121">Easing Functions</span></span>  
  
     <span data-ttu-id="da0d2-122">Animasyon davranışını üzerinde ek denetime hareket hızı işlevleri ile animasyonları geliştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="da0d2-122">You can enhance animations with easing functions, which give you additional control over the behavior of animations.</span></span> <span data-ttu-id="da0d2-123">Örneğin, geçerli bir <xref:System.Windows.Media.Animation.ElasticEase> animasyonun animasyonun esnek bir davranış vermek için.</span><span class="sxs-lookup"><span data-stu-id="da0d2-123">For example, you can apply an <xref:System.Windows.Media.Animation.ElasticEase> to an animation to give the animation a springy behavior.</span></span> <span data-ttu-id="da0d2-124">Daha fazla bilgi için bkz: hareket hızı türlerinde <xref:System.Windows.Media.Animation> ad alanı.</span><span class="sxs-lookup"><span data-stu-id="da0d2-124">For more information, see the easing types in the <xref:System.Windows.Media.Animation> namespace.</span></span>  
  
<a name="graphics_and_rendering"></a>   
## <a name="graphics-and-rendering"></a><span data-ttu-id="da0d2-125">Grafikler ve işleme</span><span class="sxs-lookup"><span data-stu-id="da0d2-125">Graphics and Rendering</span></span>  
 <span data-ttu-id="da0d2-126">WPF yüksek kaliteli 2B grafik için destek içerir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-126">WPF includes support for high quality 2-D graphics.</span></span> <span data-ttu-id="da0d2-127">İşlev Fırçalar, geometri, görüntüler, şekiller ve dönüşümler içerir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-127">The functionality includes brushes, geometries, images, shapes and transformations.</span></span> <span data-ttu-id="da0d2-128">Daha fazla bilgi için bkz: [grafik](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-128">For more information, see [Graphics](../../../../docs/framework/wpf/graphics-multimedia/graphics.md).</span></span> <span data-ttu-id="da0d2-129">Grafik öğelerin işlenmesi dayanır <xref:System.Windows.Media.Visual> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="da0d2-129">The rendering of graphical elements is based on the <xref:System.Windows.Media.Visual> class.</span></span> <span data-ttu-id="da0d2-130">Ekranında visual nesnelerin yapısı görsel ağaç tarafından tanımlanır.</span><span class="sxs-lookup"><span data-stu-id="da0d2-130">The structure of visual objects on the screen is described by the visual tree.</span></span> <span data-ttu-id="da0d2-131">Daha fazla bilgi için bkz: [WPF Grafik işleme genel bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-131">For more information, see [WPF Graphics Rendering Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).</span></span>  
  
### <a name="2-d-shapes"></a><span data-ttu-id="da0d2-132">2B şekiller</span><span class="sxs-lookup"><span data-stu-id="da0d2-132">2-D Shapes</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="da0d2-133">yaygın olarak kullanılan, vektör çizilmiş kitaplığını sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] dikdörtgenler ve aşağıda gösterilmiştir elipsler gibi şekiller.</span><span class="sxs-lookup"><span data-stu-id="da0d2-133"> provides a library of commonly used, vector-drawn [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes, such as rectangles and ellipses, which the following illustration shows.</span></span>  
  
 <span data-ttu-id="da0d2-134">![Elipsler ve dikdörtgenler](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span><span class="sxs-lookup"><span data-stu-id="da0d2-134">![Ellipses and rectangles](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure4.PNG "WPFIntroFigure4")</span></span>  
  
 <span data-ttu-id="da0d2-135">Bu iç [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] şekilleri yalnızca şekil değil: Bunlar, klavye ve fare girişi içeren, en sık kullanılan denetimlerden beklediğiniz özelliklerin çoğunu uygulayan programlanabilir öğelerdir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-135">These intrinsic [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] shapes are not just shapes: they are programmable elements that implement many of the features that you expect from most common controls, which include keyboard and mouse input.</span></span> <span data-ttu-id="da0d2-136">Aşağıdaki örnekte nasıl işleneceğini gösterir <xref:System.Windows.UIElement.MouseUp> olay gerçekleşti tıklayarak bir <xref:System.Windows.Shapes.Ellipse> öğesi.</span><span class="sxs-lookup"><span data-stu-id="da0d2-136">The following example shows how to handle the <xref:System.Windows.UIElement.MouseUp> event raised by clicking an <xref:System.Windows.Shapes.Ellipse> element.</span></span>  
  
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
  
 <span data-ttu-id="da0d2-137">Aşağıdaki şekilde önceki çıktı gösterilmiştir [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] biçimlendirme ve arka plan kodu.</span><span class="sxs-lookup"><span data-stu-id="da0d2-137">The following illustration shows the output for the preceding [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] markup and code-behind.</span></span>  
  
 <span data-ttu-id="da0d2-138">![Metinle "elips &#33; tıkladığınız" penceresi ] (../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span><span class="sxs-lookup"><span data-stu-id="da0d2-138">![A window with the text "you clicked the ellipse&#33;"](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure12.png "WPFIntroFigure12")</span></span>  
  
 <span data-ttu-id="da0d2-139">Daha fazla bilgi için bkz: [şekilleri ve WPF genel bakış temel çizim](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-139">For more information, see [Shapes and Basic Drawing in WPF Overview](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md).</span></span> <span data-ttu-id="da0d2-140">Tanıtıcı bir örnek için bkz: [şekil öğeleri örneği](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="da0d2-140">For an introductory sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
### <a name="2-d-geometries"></a><span data-ttu-id="da0d2-141">2-D geometri</span><span class="sxs-lookup"><span data-stu-id="da0d2-141">2-D Geometries</span></span>  
 <span data-ttu-id="da0d2-142">Zaman [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] şekiller [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] sağlar kullanabileceğiniz yeterli [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] geometri ve kendi oluşturmak için yollar için desteği.</span><span class="sxs-lookup"><span data-stu-id="da0d2-142">When the [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] shapes that [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides are not sufficient, you can use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] support for geometries and paths to create your own.</span></span> <span data-ttu-id="da0d2-143">Aşağıdaki çizimde, şekiller çizme fırça olarak oluşturmak ve diğer küçük geometri nasıl kullanabileceğinizi gösterir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] öğeleri.</span><span class="sxs-lookup"><span data-stu-id="da0d2-143">The following illustration shows how you can use geometries to create shapes, as a drawing brush, and to clip other [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] elements.</span></span>  
  
 <span data-ttu-id="da0d2-144">![Bir yol çeşitli kullanımları](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span><span class="sxs-lookup"><span data-stu-id="da0d2-144">![Various uses of a Path](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure5.PNG "WPFIntroFigure5")</span></span>  
  
 <span data-ttu-id="da0d2-145">Daha fazla bilgi için bkz: [geometrisi](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-145">For more information, see [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span> <span data-ttu-id="da0d2-146">Tanıtıcı bir örnek için bkz: [geometri örneği](http://go.microsoft.com/fwlink/?LinkID=159989).</span><span class="sxs-lookup"><span data-stu-id="da0d2-146">For an introductory sample, see [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
### <a name="2-d-effects"></a><span data-ttu-id="da0d2-147">2B efektler</span><span class="sxs-lookup"><span data-stu-id="da0d2-147">2-D Effects</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="da0d2-148">kitaplığını sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] çeşitli efektler oluşturmak için kullanabileceğiniz sınıfları.</span><span class="sxs-lookup"><span data-stu-id="da0d2-148"> provides a library of [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] classes that you can use to create a variety of effects.</span></span> <span data-ttu-id="da0d2-149">[!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] İşleme yeteneğini [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] boyamak olanağı sağlar [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] gradyan, bit eşlemler, çizimler ve videolar; olan öğenin ve döndürme, kullanarak işlemek için ölçekleme ve eğriltme.</span><span class="sxs-lookup"><span data-stu-id="da0d2-149">The [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] rendering capability of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] provides the ability to paint [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] elements that have gradients, bitmaps, drawings, and videos; and to manipulate them by using rotation, scaling, and skewing.</span></span> <span data-ttu-id="da0d2-150">Aşağıdaki çizim bir örnek kullanarak elde edebileceğiniz birçok etkileri verir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] Fırçalar.</span><span class="sxs-lookup"><span data-stu-id="da0d2-150">The following illustration gives an example of the many effects you can achieve by using [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] brushes.</span></span>  
  
 <span data-ttu-id="da0d2-151">![Farklı fırçalar çizimi](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span><span class="sxs-lookup"><span data-stu-id="da0d2-151">![Illustration of different brushes](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure6.PNG "WPFIntroFigure6")</span></span>  
  
 <span data-ttu-id="da0d2-152">Daha fazla bilgi için bkz: [WPF Fırçaları Genel Bakış](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-152">For more information, see [WPF Brushes Overview](../../../../docs/framework/wpf/graphics-multimedia/wpf-brushes-overview.md).</span></span> <span data-ttu-id="da0d2-153">Tanıtıcı bir örnek için bkz: [Fırçalar örnek](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="da0d2-153">For an introductory sample, see [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
<a name="rendering"></a>   
## <a name="3-d-rendering"></a><span data-ttu-id="da0d2-154">3B işleme</span><span class="sxs-lookup"><span data-stu-id="da0d2-154">3-D Rendering</span></span>  
 [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]<span data-ttu-id="da0d2-155">bir dizi sağlar [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] tümleştirileceğini işleme yeteneklerini [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] grafik desteği [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] daha heyecan verici bir düzen oluşturmak için sırayla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ve veri görselleştirme.</span><span class="sxs-lookup"><span data-stu-id="da0d2-155"> provides a set of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] rendering capabilities that integrate with [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] graphics support in [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] in order for you to create more exciting layout, [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], and data visualization.</span></span> <span data-ttu-id="da0d2-156">Spektrumun bir ucunda [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] işlenecek sağlar [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] yüzeyleriyle görüntüleri [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] şekiller, aşağıdaki çizimde gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-156">At one end of the spectrum, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to render [!INCLUDE[TLA2#tla_2d](../../../../includes/tla2sharptla-2d-md.md)] images onto the surfaces of [!INCLUDE[TLA2#tla_3d](../../../../includes/tla2sharptla-3d-md.md)] shapes, which the following illustration demonstrates.</span></span>  
  
 <span data-ttu-id="da0d2-157">![Visual3D örnek ekran görüntüsü](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span><span class="sxs-lookup"><span data-stu-id="da0d2-157">![Visual3D sample screen shot](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure13.png "WPFIntroFigure13")</span></span>  
  
 <span data-ttu-id="da0d2-158">Daha fazla bilgi için bkz: [3-b grafiklere genel bakış](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-158">For more information, see [3-D Graphics Overview](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md).</span></span> <span data-ttu-id="da0d2-159">Tanıtıcı bir örnek için bkz: [3-b düz çizgi örneği](http://go.microsoft.com/fwlink/?LinkID=159964).</span><span class="sxs-lookup"><span data-stu-id="da0d2-159">For an introductory sample, see [3-D Solids Sample](http://go.microsoft.com/fwlink/?LinkID=159964).</span></span>  
  
<a name="animation"></a>   
## <a name="animation"></a><span data-ttu-id="da0d2-160">Animasyon</span><span class="sxs-lookup"><span data-stu-id="da0d2-160">Animation</span></span>  
 <span data-ttu-id="da0d2-161">Animasyon denetimleri ve büyüme, sallama, döndürme ve silinerek öğeleri yapmak için kullanın; ve ilginç sayfa geçişleri ve daha fazlasını oluşturun.</span><span class="sxs-lookup"><span data-stu-id="da0d2-161">Use animation to make controls and elements grow, shake, spin, and fade; and to create interesting page transitions, and more.</span></span> <span data-ttu-id="da0d2-162">Çünkü [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] özelliklerinin çoğu, yalnızca animasyon eklemek için şunları yapabilirsiniz etkinleştirir, çoğu hareketli hale getirmeyi [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] nesnelerini de kullanabilir [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] oluşturduğunuz özel nesnelere animasyon uygulamak.</span><span class="sxs-lookup"><span data-stu-id="da0d2-162">Because [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] enables you to animate most properties, not only can you animate most [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] objects, you can also use [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] to animate custom objects that you create.</span></span>  
  
 <span data-ttu-id="da0d2-163">![Animasyonlu bir küpü görüntülerini](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span><span class="sxs-lookup"><span data-stu-id="da0d2-163">![Images of an animated cube](../../../../docs/framework/wpf/graphics-multimedia/media/wpfintrofigure7.png "WPFIntroFigure7")</span></span>  
  
 <span data-ttu-id="da0d2-164">Daha fazla bilgi için bkz: [animasyon genel bakış](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-164">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).</span></span> <span data-ttu-id="da0d2-165">Tanıtıcı bir örnek için bkz: [animasyon örnek Galerisi](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="da0d2-165">For an introductory sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
<a name="media"></a>   
## <a name="media"></a><span data-ttu-id="da0d2-166">Medya</span><span class="sxs-lookup"><span data-stu-id="da0d2-166">Media</span></span>  
 <span data-ttu-id="da0d2-167">Resim, video ve ses bilgileri ve kullanıcı deneyimlerini aktaran, medya zengin yöntemleridir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-167">Images, video, and audio are media-rich ways of conveying information and user experiences.</span></span>  
  
### <a name="images"></a><span data-ttu-id="da0d2-168">Görüntüler</span><span class="sxs-lookup"><span data-stu-id="da0d2-168">Images</span></span>  
 <span data-ttu-id="da0d2-169">Simgeler, arka planlar ve hatta animasyonların bölümleri içerir, görüntüleri çoğu uygulamayı çekirdek parçasıdır.</span><span class="sxs-lookup"><span data-stu-id="da0d2-169">Images, which include icons, backgrounds, and even parts of animations, are a core part of most applications.</span></span> <span data-ttu-id="da0d2-170">Sık görüntüleri kullanmak gerektiğinden [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] çeşitli şekillerde onlarla çalışma olanağı sunar.</span><span class="sxs-lookup"><span data-stu-id="da0d2-170">Because you frequently need to use images, [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] exposes the ability to work with them in a variety of ways.</span></span> <span data-ttu-id="da0d2-171">Aşağıda bu yollardan biri gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-171">The following illustration shows just one of those ways.</span></span>  
  
 <span data-ttu-id="da0d2-172">![Stil örnek ekran görüntüsü](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span><span class="sxs-lookup"><span data-stu-id="da0d2-172">![Styling sample screen shot](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")</span></span>  
  
 <span data-ttu-id="da0d2-173">Daha fazla bilgi için bkz: [Imaging genel bakış](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-173">For more information, see [Imaging Overview](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md).</span></span>  
  
### <a name="video-and-audio"></a><span data-ttu-id="da0d2-174">Video ve ses</span><span class="sxs-lookup"><span data-stu-id="da0d2-174">Video and Audio</span></span>  
 <span data-ttu-id="da0d2-175">Grafik özelliklerini çekirdek özelliği [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] video ve ses içeren çoklu ortam ile çalışmak için yerel destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="da0d2-175">A core feature of the graphics capabilities of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] is to provide native support for working with multimedia, which includes video and audio.</span></span> <span data-ttu-id="da0d2-176">Aşağıdaki örnek bir medya oynatıcı bir uygulamaya eklemek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="da0d2-176">The following example shows how to insert a media player into an application.</span></span>  
  
```xaml  
<MediaElement Source="media\numbers.wmv" Width="450" Height="250" />  
```  
  
 <span data-ttu-id="da0d2-177"><xref:System.Windows.Controls.MediaElement>video ve ses çalma yeteneğine sahiptir ve özel kolay oluşturulmasına izin için Genişletilebilir [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="da0d2-177"><xref:System.Windows.Controls.MediaElement> is capable of playing both video and audio, and is extensible enough to allow the easy creation of custom [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)].</span></span>  
  
 <span data-ttu-id="da0d2-178">Daha fazla bilgi için bkz: [multimedya genel bakış](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).</span><span class="sxs-lookup"><span data-stu-id="da0d2-178">For more information, see the [Multimedia Overview](../../../../docs/framework/wpf/graphics-multimedia/multimedia-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0d2-179">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="da0d2-179">See Also</span></span>  
 <xref:System.Windows.Media>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Media3D>  
 [<span data-ttu-id="da0d2-180">2B Grafikleri ve Görüntüleme</span><span class="sxs-lookup"><span data-stu-id="da0d2-180">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="da0d2-181">WPF’de Şekiller ve Temel Çizimlere Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="da0d2-181">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="da0d2-182">Düz Renkler ve Gradyanlar ile Boyamaya Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="da0d2-182">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="da0d2-183">Görüntüler, Çizimler ve Görsellerle Boyama</span><span class="sxs-lookup"><span data-stu-id="da0d2-183">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)  
 [<span data-ttu-id="da0d2-184">Animasyon ve zamanlama</span><span class="sxs-lookup"><span data-stu-id="da0d2-184">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="da0d2-185">3B grafik</span><span class="sxs-lookup"><span data-stu-id="da0d2-185">3-D Graphics</span></span>](http://msdn.microsoft.com/library/565c1f3c-235b-47de-b05b-3b53ed63f1b8)  
 [<span data-ttu-id="da0d2-186">Multimedya</span><span class="sxs-lookup"><span data-stu-id="da0d2-186">Multimedia</span></span>](http://msdn.microsoft.com/library/44a8dcd0-80cb-4db0-a222-87cde68c2fac)
