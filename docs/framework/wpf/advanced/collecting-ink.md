---
title: "Mürekkep Toplama"
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
- ink [WPF], collecting
- InkCanvas element [WPF]
- properties [WPF], DrawingAttributes
- collecting digital ink [WPF]
- digital ink [WPF], collecting
- properties [WPF], DefaultDrawingAttributes
- DefaultDrawingAttributes property [WPF]
ms.assetid: 66a3129d-9577-43eb-acbd-56c147282016
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cbf55b5d84420a6aa7af06e94497a85a2b54a0c0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="collecting-ink"></a><span data-ttu-id="054b9-102">Mürekkep Toplama</span><span class="sxs-lookup"><span data-stu-id="054b9-102">Collecting Ink</span></span>
<span data-ttu-id="054b9-103">[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform dijital mürekkep işlevselliğini önemli bir parçası toplar.</span><span class="sxs-lookup"><span data-stu-id="054b9-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="054b9-104">Bu konu içinde mürekkep topluluğu için yöntemleri anlatır [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].</span><span class="sxs-lookup"><span data-stu-id="054b9-104">This topic discusses methods for collection of ink in [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)].</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="054b9-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="054b9-105">Prerequisites</span></span>  
 <span data-ttu-id="054b9-106">Aşağıdaki örnekler kullanmak için önce yüklemelisiniz [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] ve [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="054b9-106">To use the following examples, you must first install [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)] and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="054b9-107">Uygulamaları yazmak nasıl anlamanız gerekir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="054b9-107">You should also understand how to write applications for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="054b9-108">İle çalışmaya başlama hakkında daha fazla bilgi için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], bkz: [gözden geçirme: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="054b9-108">For more information about getting started with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>  
  
## <a name="using-the-inkcanvas-element"></a><span data-ttu-id="054b9-109">InkCanvas öğesi kullanma</span><span class="sxs-lookup"><span data-stu-id="054b9-109">Using the InkCanvas Element</span></span>  
 <span data-ttu-id="054b9-110"><xref:System.Windows.Controls.InkCanvas> Öğesi sağlar mürekkep toplamak için en kolay yolu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="054b9-110">The <xref:System.Windows.Controls.InkCanvas> element provides the easiest way to collect ink in [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span> <span data-ttu-id="054b9-111"><xref:System.Windows.Controls.InkCanvas> Öğesi benzer [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) nesnesinin [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] ve önceki sürümleri.</span><span class="sxs-lookup"><span data-stu-id="054b9-111">The <xref:System.Windows.Controls.InkCanvas> element is similar to the [Microsoft.Ink.InkOverlay](https://msdn.microsoft.com/library/microsoft.ink.inkoverlay\(v=vs.90\).aspx) object from the [!INCLUDE[TLA2#tla_tpclssdk](../../../../includes/tla2sharptla-tpclssdk-md.md)] and earlier versions.</span></span>  
  
 <span data-ttu-id="054b9-112">Kullanım bir <xref:System.Windows.Controls.InkCanvas> mürekkep girişi almak ve görüntülemek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="054b9-112">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="054b9-113">Yaygın olarak mürekkep mürekkep vuruşları üretmek için dönüştürücü ile etkileşime giren bir kalem kullanımı ile de girin.</span><span class="sxs-lookup"><span data-stu-id="054b9-113">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="054b9-114">Ayrıca, fare kalem yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="054b9-114">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="054b9-115">Oluşturulan vuruşları olarak temsil edilir <xref:System.Windows.Ink.Stroke> nesneleri ve hem program aracılığıyla kullanıcı girişi tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="054b9-115">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="054b9-116"><xref:System.Windows.Controls.InkCanvas> Seçin, değiştirin veya varolan bir silmek kullanıcıların sağlayan <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="054b9-116">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>  
  
 <span data-ttu-id="054b9-117">XAML kullanarak mürekkep koleksiyonunu eklediğiniz gibi kolayca ayarlayabileceğiniz bir `InkCanvas` , ağaç öğesi.</span><span class="sxs-lookup"><span data-stu-id="054b9-117">By using XAML, you can set up ink collection as easily as adding an `InkCanvas` element to your tree.</span></span> <span data-ttu-id="054b9-118">Aşağıdaki örnek, bir <xref:System.Windows.Controls.InkCanvas> varsayılan bir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] oluşturulan proje [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].</span><span class="sxs-lookup"><span data-stu-id="054b9-118">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project created in [!INCLUDE[TLA#tla_visualstu2005](../../../../includes/tlasharptla-visualstu2005-md.md)].</span></span>  
  
 [!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]  
  
 <span data-ttu-id="054b9-119">`InkCanvas` Öğesi, alt öğeler, neredeyse her tür XAML öğesine mürekkep ek açıklama özellikleri eklemek olası hale getirerek de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="054b9-119">The `InkCanvas` element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="054b9-120">Örneğin, bir metin öğesine mürekkep özelliklerini eklemek için yalnızca bir alt kolaylaştırır bir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="054b9-120">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>.</span></span>  
  
 [!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]  
  
 <span data-ttu-id="054b9-121">Bir resmi mürekkep ile işaretleme desteği ekleme oldukça kolaydır.</span><span class="sxs-lookup"><span data-stu-id="054b9-121">Adding support for marking up an image with ink is just as easy.</span></span>  
  
 [!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]  
  
### <a name="inkcollection-modes"></a><span data-ttu-id="054b9-122">InkCollection Modları</span><span class="sxs-lookup"><span data-stu-id="054b9-122">InkCollection Modes</span></span>  
 <span data-ttu-id="054b9-123"><xref:System.Windows.Controls.InkCanvas> Aracılığıyla çeşitli giriş modları için destek sağlar, <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="054b9-123">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>  
  
### <a name="manipulating-ink"></a><span data-ttu-id="054b9-124">Mürekkep düzenleme</span><span class="sxs-lookup"><span data-stu-id="054b9-124">Manipulating Ink</span></span>  
 <span data-ttu-id="054b9-125"><xref:System.Windows.Controls.InkCanvas> Birçok mürekkep düzenleme işlemleri için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="054b9-125">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="054b9-126">Örneğin, <xref:System.Windows.Controls.InkCanvas> destekler geri kalem arkası silme işlevselliği öğesine eklemek için gereken ek kod olmadan.</span><span class="sxs-lookup"><span data-stu-id="054b9-126">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase with no additional code needed to add the functionality to the element.</span></span>  
  
#### <a name="selection"></a><span data-ttu-id="054b9-127">Seçim</span><span class="sxs-lookup"><span data-stu-id="054b9-127">Selection</span></span>  
 <span data-ttu-id="054b9-128">Seçim modunu ayarlama ayarı olarak basit <xref:System.Windows.Controls.InkCanvasEditingMode> özelliğine **seçin**.</span><span class="sxs-lookup"><span data-stu-id="054b9-128">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span> <span data-ttu-id="054b9-129">Aşağıdaki kod değerine göre düzenleme modunu ayarlar bir <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="054b9-129">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>  
  
 [!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
 [!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]  
  
#### <a name="drawingattributes"></a><span data-ttu-id="054b9-130">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="054b9-130">DrawingAttributes</span></span>  
 <span data-ttu-id="054b9-131">Kullanım <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> mürekkep vuruşları görünümünü değiştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="054b9-131">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="054b9-132">Örneğin, <xref:System.Windows.Ink.DrawingAttributes.Color%2A> üyesi <xref:System.Windows.Ink.DrawingAttributes> işlenen rengini ayarlar <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="054b9-132">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span> <span data-ttu-id="054b9-133">Aşağıdaki örnek, seçili vuruşları rengi kırmızı değiştirir.</span><span class="sxs-lookup"><span data-stu-id="054b9-133">The following example changes the color of the selected strokes to red.</span></span>  
  
 [!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
 [!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]  
  
### <a name="defaultdrawingattributes"></a><span data-ttu-id="054b9-134">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="054b9-134">DefaultDrawingAttributes</span></span>  
 <span data-ttu-id="054b9-135"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Özelliği yüksekliğini, genişlik ve oluşturulması için vuruşları rengi gibi özelliklere erişim sağlar bir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="054b9-135">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="054b9-136">Kere değiştirdiğinizde <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, girilen tüm gelecekteki vuruşları <xref:System.Windows.Controls.InkCanvas> yeni özellik değerleri ile işlenir.</span><span class="sxs-lookup"><span data-stu-id="054b9-136">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>  
  
 <span data-ttu-id="054b9-137">Değiştirme yanı sıra <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> arka plan kod dosyasına belirtmek için XAML sözdizimini kullanabilirsiniz <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="054b9-137">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span> <span data-ttu-id="054b9-138">Aşağıdaki XAML kodu nasıl ayarlanacağını gösterir <xref:System.Windows.Ink.DrawingAttributes.Color%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="054b9-138">The following XAML code demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="054b9-139">Bu kodu kullanmak için yeni bir oluşturma [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Visual Studio 2005'te "HelloInkCanvas" adlı projesi.</span><span class="sxs-lookup"><span data-stu-id="054b9-139">To use this code, create a new [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] project called "HelloInkCanvas" in Visual Studio 2005.</span></span> <span data-ttu-id="054b9-140">Window1.xaml dosyasındaki kodu aşağıdaki kodla değiştirin.</span><span class="sxs-lookup"><span data-stu-id="054b9-140">Replace the code in the Window1.xaml file with the following code.</span></span>  
  
 [!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="054b9-141">Ardından, Window1 sınıfı içindeki dosyanın arkasındaki kodda aşağıdaki düğmesi olay işleyicileri ekleyin.</span><span class="sxs-lookup"><span data-stu-id="054b9-141">Next, add the following button event handlers to the code behind file, inside the Window1 class.</span></span>  
  
 [!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]  
  
 <span data-ttu-id="054b9-142">Bu kodu kopyaladıktan sonra basın **F5** Microsoft Visual Studio 2005 hata ayıklayıcıda programı çalıştırmak için.</span><span class="sxs-lookup"><span data-stu-id="054b9-142">After copying this code, press **F5** in Microsoft Visual Studio 2005 to run the program in the debugger.</span></span>  
  
 <span data-ttu-id="054b9-143">Bildirim nasıl <xref:System.Windows.Controls.StackPanel> düğmeleri üstüne yerleştirir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="054b9-143">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="054b9-144">Düğmeleri üst mürekkep çalışırsanız <xref:System.Windows.Controls.InkCanvas> mürekkep düğmelerin arkasında işler ve toplar.</span><span class="sxs-lookup"><span data-stu-id="054b9-144">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="054b9-145">Düğmeleri eşdüzey öğelerinin olmasıdır <xref:System.Windows.Controls.InkCanvas> alt aksine.</span><span class="sxs-lookup"><span data-stu-id="054b9-145">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="054b9-146">Ayrıca, mürekkep arkasına çizilir şekilde düğmeleri z sırayla daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="054b9-146">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="054b9-147">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="054b9-147">See Also</span></span>  
 <xref:System.Windows.Ink.DrawingAttributes>  
 <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>  
 <xref:System.Windows.Ink>
