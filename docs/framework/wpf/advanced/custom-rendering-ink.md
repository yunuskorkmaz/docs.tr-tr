---
title: Özel İşleme Mürekkebi
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom-rendering ink
- ink [WPF], custom-rendering
- classes [WPF], InkCanvas
ms.assetid: 65c978a7-0ee0-454f-ac7f-b1bd2efecac5
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e8f7288d9d3b729ab9c38bc6b2afd603b4d6d1aa
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/30/2018
---
# <a name="custom-rendering-ink"></a><span data-ttu-id="95f4b-102">Özel İşleme Mürekkebi</span><span class="sxs-lookup"><span data-stu-id="95f4b-102">Custom Rendering Ink</span></span>
<span data-ttu-id="95f4b-103"><xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> Vuruş özelliğinin boyutunu, rengini ve şekil gibi bir vuruş görünümünü belirtmenize olanak verir, ancak ne ötesinde görünümünü özelleştirmek istediğiniz zamanlar olabilir <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> izin verin.</span><span class="sxs-lookup"><span data-stu-id="95f4b-103">The <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property of a stroke allows you to specify the appearance of a stroke, such as its size, color, and shape, but there may be times that you want to customize the appearance beyond what <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> allow.</span></span> <span data-ttu-id="95f4b-104">Hava fırça, Petrol boyama ve diğer birçok efekt görünümünü işlemede tarafından mürekkep görünümünü özelleştirmek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f4b-104">You may want to customize the appearance of ink by rendering in the appearance of an air brush, oil paint, and many other effects.</span></span> <span data-ttu-id="95f4b-105">Windows Presentation Foundation (WPF), özel işleme mürekkep özel bir uygulama tarafından verir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve <xref:System.Windows.Ink.Stroke> nesne.</span><span class="sxs-lookup"><span data-stu-id="95f4b-105">The Windows Presentation Foundation (WPF) allows you to custom render ink by implementing a custom <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and <xref:System.Windows.Ink.Stroke> object.</span></span>  
  
 <span data-ttu-id="95f4b-106">Bu konu, aşağıdaki alt bölümleri içerir:</span><span class="sxs-lookup"><span data-stu-id="95f4b-106">This topic contains the following subsections:</span></span>  
  
-   [<span data-ttu-id="95f4b-107">Mimari</span><span class="sxs-lookup"><span data-stu-id="95f4b-107">Architecture</span></span>](#Architecture)  
  
-   [<span data-ttu-id="95f4b-108">Dinamik işleyici uygulama</span><span class="sxs-lookup"><span data-stu-id="95f4b-108">Implementing a Dynamic Renderer</span></span>](#ImplementingADynamicRenderer)  
  
-   [<span data-ttu-id="95f4b-109">Özel vuruşları uygulama</span><span class="sxs-lookup"><span data-stu-id="95f4b-109">Implementing Custom Strokes</span></span>](#ImplementingCustomStrokes)  
  
-   [<span data-ttu-id="95f4b-110">Özel InkCanvas Uygulama</span><span class="sxs-lookup"><span data-stu-id="95f4b-110">Implementing a Custom InkCanvas</span></span>](#ImplementingACustomInkCanvas)  
  
-   [<span data-ttu-id="95f4b-111">Sonuç</span><span class="sxs-lookup"><span data-stu-id="95f4b-111">Conclusion</span></span>](#Conclusion)  
  
<a name="Architecture"></a>   
## <a name="architecture"></a><span data-ttu-id="95f4b-112">Mimari</span><span class="sxs-lookup"><span data-stu-id="95f4b-112">Architecture</span></span>  
 <span data-ttu-id="95f4b-113">Mürekkep işleme iki kez oluşan; bir kullanıcı mürekkep yüzeyine ve vuruşun sonra yeniden yazdığında mürekkep etkin yüzeye eklenir.</span><span class="sxs-lookup"><span data-stu-id="95f4b-113">Ink rendering occurs two times; when a user writes ink to an inking surface, and again after the stroke is added to the ink-enabled surface.</span></span> <span data-ttu-id="95f4b-114"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> Kullanıcı dijital dönüştürücü üzerinde tablet kalem taşıdığında mürekkep işler ve <xref:System.Windows.Ink.Stroke> bir öğe olarak eklendikten sonra kendisini işler.</span><span class="sxs-lookup"><span data-stu-id="95f4b-114">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> renders the ink when the user moves the tablet pen on the digitizer, and the <xref:System.Windows.Ink.Stroke> renders itself once it is added to an element.</span></span>  
  
 <span data-ttu-id="95f4b-115">Mürekkep dinamik olarak işlenirken uygulamak için üç sınıfları vardır.</span><span class="sxs-lookup"><span data-stu-id="95f4b-115">There are three classes to implement when dynamically rendering ink.</span></span>  
  
1.  <span data-ttu-id="95f4b-116">**DynamicRenderer**: türeyen bir sınıf uygulama <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span><span class="sxs-lookup"><span data-stu-id="95f4b-116">**DynamicRenderer**: Implement a class that derives from <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="95f4b-117">Bu sınıf özelleştirilmiş, <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> çizilirken vuruşun işleyen.</span><span class="sxs-lookup"><span data-stu-id="95f4b-117">This class is a specialized <xref:System.Windows.Input.StylusPlugIns.StylusPlugIn> that renders the stroke as it is drawn.</span></span> <span data-ttu-id="95f4b-118"><xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> İçindekine yüzeyini uygulama kullanıcı arabirimi (UI) iş parçacığı engellendiğinde bile mürekkep toplamak görünmesi için ayrı bir iş parçacığı üzerinde işlemeyi yapar.</span><span class="sxs-lookup"><span data-stu-id="95f4b-118">The <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> does the rendering on a separate thread, so the inking surface appears to collect ink even when the application user interface (UI) thread is blocked.</span></span> <span data-ttu-id="95f4b-119">İş parçacığı modeli hakkında daha fazla bilgi için bkz: [mürekkep iş parçacığı modeli](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).</span><span class="sxs-lookup"><span data-stu-id="95f4b-119">For more information about the threading model, see [The Ink Threading Model](../../../../docs/framework/wpf/advanced/the-ink-threading-model.md).</span></span> <span data-ttu-id="95f4b-120">Dinamik olarak vuruş işleme özelleştirmek için geçersiz kılma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95f4b-120">To customize dynamically rendering a stroke, override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
2.  <span data-ttu-id="95f4b-121">**Vuruş**: türeyen bir sınıf uygulama <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="95f4b-121">**Stroke**: Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="95f4b-122">Bu sınıf, statik işlenmesinden sorumludur <xref:System.Windows.Input.StylusPoint> içine dönüştürüldükten sonra verileri bir <xref:System.Windows.Ink.Stroke> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="95f4b-122">This class is responsible for static rendering of the <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="95f4b-123">Geçersiz kılma <xref:System.Windows.Ink.Stroke.DrawCore%2A> Vuruşun statik işlemesinin emin olmak için yöntem dinamik işlemesi ile tutarlıdır.</span><span class="sxs-lookup"><span data-stu-id="95f4b-123">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> method to ensure that static rendering of the stroke is consistent with dynamic rendering.</span></span>  
  
3.  <span data-ttu-id="95f4b-124">**InkCanvas:** türeyen bir sınıf uygulama <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="95f4b-124">**InkCanvas:** Implement a class that derives from <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="95f4b-125">Özelleştirilmiş atamak <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="95f4b-125">Assign the customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property.</span></span> <span data-ttu-id="95f4b-126">Geçersiz kılma <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> yöntemi ve özel bir vuruş ekleyin <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="95f4b-126">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method and add a custom stroke to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property.</span></span> <span data-ttu-id="95f4b-127">Bu mürekkep görünümünü tutarlı olmasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="95f4b-127">This ensures that the appearance of the ink is consistent.</span></span>  
  
<a name="ImplementingADynamicRenderer"></a>   
## <a name="implementing-a-dynamic-renderer"></a><span data-ttu-id="95f4b-128">Dinamik işleyici uygulama</span><span class="sxs-lookup"><span data-stu-id="95f4b-128">Implementing a Dynamic Renderer</span></span>  
 <span data-ttu-id="95f4b-129">Rağmen <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> sınıfı, standart bir parçası [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], özelleştirilmiş işlemeyi daha gerçekleştirmek için türetilen özelleştirilmiş dinamik işleyicisini oluşturmalısınız <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve geçersiz kılma <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95f4b-129">Although the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> class is a standard part of [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], to perform more specialized rendering, you must create a customized dynamic renderer that derives from the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and override the <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer.OnDraw%2A> method.</span></span>  
  
 <span data-ttu-id="95f4b-130">Aşağıdaki örnek özelleştirilmiş gösterir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> mürekkep doğrusal gradyan fırçası etkisi olmadan çizer.</span><span class="sxs-lookup"><span data-stu-id="95f4b-130">The following example demonstrates a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> that draws ink with a linear gradient brush effect.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#1)]
[!code-vb[AdvancedInkTopicsSamples#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#1)]  
  
<a name="ImplementingCustomStrokes"></a>   
## <a name="implementing-custom-strokes"></a><span data-ttu-id="95f4b-131">Özel vuruşları uygulama</span><span class="sxs-lookup"><span data-stu-id="95f4b-131">Implementing Custom Strokes</span></span>  
 <span data-ttu-id="95f4b-132">Türeyen bir sınıf uygulama <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="95f4b-132">Implement a class that derives from <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="95f4b-133">Bu sınıf işlenmesinden sorumludur <xref:System.Windows.Input.StylusPoint> içine dönüştürüldükten sonra verileri bir <xref:System.Windows.Ink.Stroke> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="95f4b-133">This class is responsible for rendering <xref:System.Windows.Input.StylusPoint> data after it has been converted into a <xref:System.Windows.Ink.Stroke> object.</span></span> <span data-ttu-id="95f4b-134">Geçersiz kılma <xref:System.Windows.Ink.Stroke.DrawCore%2A> Fiili çizimi yapmak için sınıf.</span><span class="sxs-lookup"><span data-stu-id="95f4b-134">Override the <xref:System.Windows.Ink.Stroke.DrawCore%2A> class to do the actual drawing.</span></span>  
  
 <span data-ttu-id="95f4b-135">Stroke sınıfınız ayrıca özel verileri kullanarak depolayabilir <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95f4b-135">Your Stroke class can also store custom data by using the <xref:System.Windows.Ink.Stroke.AddPropertyData%2A> method.</span></span> <span data-ttu-id="95f4b-136">Bu veriler kalıcı olduğunda vuruş verisi ile depolanır.</span><span class="sxs-lookup"><span data-stu-id="95f4b-136">This data is stored with the stroke data when persisted.</span></span>  
  
 <span data-ttu-id="95f4b-137"><xref:System.Windows.Ink.Stroke> Sınıfı, isabet testi de gerçekleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="95f4b-137">The <xref:System.Windows.Ink.Stroke> class can also perform hit testing.</span></span> <span data-ttu-id="95f4b-138">Algoritma kılarak kendi isabet sınama de uygulayabilir <xref:System.Windows.Ink.Stroke.HitTest%2A> geçerli sınıf içinde yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95f4b-138">You can also implement your own hit testing algorithm by overriding the <xref:System.Windows.Ink.Stroke.HitTest%2A> method in the current class.</span></span>  
  
 <span data-ttu-id="95f4b-139">Aşağıdaki C# kodu özel gösterir <xref:System.Windows.Ink.Stroke> işler sınıfı <xref:System.Windows.Input.StylusPoint> verisini 3-b vuruş olarak.</span><span class="sxs-lookup"><span data-stu-id="95f4b-139">The following C# code demonstrates a custom <xref:System.Windows.Ink.Stroke> class that renders <xref:System.Windows.Input.StylusPoint> data as a 3-D stroke.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#19)]
 [!code-vb[AdvancedInkTopicsSamples#19](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#19)]  
[!code-csharp[AdvancedInkTopicsSamples#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/DynamicRenderer.cs#2)]
[!code-vb[AdvancedInkTopicsSamples#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AdvancedInkTopicsSamples/VisualBasic/DynamicRenderer.vb#2)]  
  
<a name="ImplementingACustomInkCanvas"></a>   
## <a name="implementing-a-custom-inkcanvas"></a><span data-ttu-id="95f4b-140">Özel InkCanvas Uygulama</span><span class="sxs-lookup"><span data-stu-id="95f4b-140">Implementing a Custom InkCanvas</span></span>  
 <span data-ttu-id="95f4b-141">Özelleştirilmiş kullanmak için en kolay yolu <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve vuruşu türeyen bir sınıf uygulama için <xref:System.Windows.Controls.InkCanvas> ve bu sınıfları kullanır.</span><span class="sxs-lookup"><span data-stu-id="95f4b-141">The easiest way to use your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and stroke is to implement a class that derives from <xref:System.Windows.Controls.InkCanvas> and uses these classes.</span></span> <span data-ttu-id="95f4b-142"><xref:System.Windows.Controls.InkCanvas> Sahip bir <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> vuruşun kullanıcı onu çizerken nasıl işleneceğini belirten özellik.</span><span class="sxs-lookup"><span data-stu-id="95f4b-142">The <xref:System.Windows.Controls.InkCanvas> has a <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A> property that specifies how the stroke is rendered when the user is drawing it.</span></span>  
  
 <span data-ttu-id="95f4b-143">Özel olarak üzerinde vuruşları işlemek bir <xref:System.Windows.Controls.InkCanvas> aşağıdakileri yapın:</span><span class="sxs-lookup"><span data-stu-id="95f4b-143">To custom render strokes on an <xref:System.Windows.Controls.InkCanvas> do the following:</span></span>  
  
-   <span data-ttu-id="95f4b-144">Türeyen bir sınıf oluşturun <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="95f4b-144">Create a class that derives from the <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
-   <span data-ttu-id="95f4b-145">Özelleştirilmiş atamak <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> için <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="95f4b-145">Assign your customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> to the <xref:System.Windows.Controls.InkCanvas.DynamicRenderer%2A?displayProperty=nameWithType> property.</span></span>  
  
-   <span data-ttu-id="95f4b-146">Geçersiz kılma <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="95f4b-146">Override the <xref:System.Windows.Controls.InkCanvas.OnStrokeCollected%2A> method.</span></span> <span data-ttu-id="95f4b-147">Bu yöntemde, InkCanvas'a eklenen özgün vuruşu kaldırın.</span><span class="sxs-lookup"><span data-stu-id="95f4b-147">In this method, remove the original stroke that was added to the InkCanvas.</span></span> <span data-ttu-id="95f4b-148">Özel bir vuruş oluşturun, ekleyin <xref:System.Windows.Controls.InkCanvas.Strokes%2A> özelliği ve çağrısı ile yeni bir temel sınıfı <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> özel vuruş içerir.</span><span class="sxs-lookup"><span data-stu-id="95f4b-148">Then create a custom stroke, add it to the <xref:System.Windows.Controls.InkCanvas.Strokes%2A> property, and call the base class with a new <xref:System.Windows.Controls.InkCanvasStrokeCollectedEventArgs> that contains the custom stroke.</span></span>  
  
 <span data-ttu-id="95f4b-149">Aşağıdaki C# kodu özel gösterir <xref:System.Windows.Controls.InkCanvas> özelleştirilmiş kullanan sınıfı <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> ve özel vuruşları toplar.</span><span class="sxs-lookup"><span data-stu-id="95f4b-149">The following C# code demonstrates a custom <xref:System.Windows.Controls.InkCanvas> class that uses a customized <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> and collects custom strokes.</span></span>  
  
 [!code-csharp[AdvancedInkTopicsSamples#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AdvancedInkTopicsSamples/CSharp/Window1.xaml.cs#9)]  
  
 <span data-ttu-id="95f4b-150">Bir <xref:System.Windows.Controls.InkCanvas> birden fazla olabilir <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span><span class="sxs-lookup"><span data-stu-id="95f4b-150">An <xref:System.Windows.Controls.InkCanvas> can have more than one <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>.</span></span> <span data-ttu-id="95f4b-151">Birden çok ekleyebilirsiniz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> nesneleri <xref:System.Windows.Controls.InkCanvas> ekleyerek <xref:System.Windows.UIElement.StylusPlugIns%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="95f4b-151">You can add multiple <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer> objects to the <xref:System.Windows.Controls.InkCanvas> by adding them to the <xref:System.Windows.UIElement.StylusPlugIns%2A> property.</span></span>  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a><span data-ttu-id="95f4b-152">Sonuç</span><span class="sxs-lookup"><span data-stu-id="95f4b-152">Conclusion</span></span>  
 <span data-ttu-id="95f4b-153">Kendi türetme mürekkep görünümünü özelleştirebilirsiniz <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, ve <xref:System.Windows.Controls.InkCanvas> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="95f4b-153">You can customize the appearance of ink by deriving your own <xref:System.Windows.Input.StylusPlugIns.DynamicRenderer>, <xref:System.Windows.Ink.Stroke>, and <xref:System.Windows.Controls.InkCanvas> classes.</span></span> <span data-ttu-id="95f4b-154">Birlikte, bu sınıfları vuruşun görünümünü vuruşun kullanıcı çizer ve toplandıktan sonra tutarlı olduğundan emin olun.</span><span class="sxs-lookup"><span data-stu-id="95f4b-154">Together, these classes ensure that the appearance of the stroke is consistent when the user draws the stroke and after it is collected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95f4b-155">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="95f4b-155">See Also</span></span>  
 [<span data-ttu-id="95f4b-156">Gelişmiş Mürekkep İşleme</span><span class="sxs-lookup"><span data-stu-id="95f4b-156">Advanced Ink Handling</span></span>](../../../../docs/framework/wpf/advanced/advanced-ink-handling.md)
