---
title: WPF uygulamalarında mürekkep toplama
ms.date: 08/15/2018
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
ms.openlocfilehash: 25f9c0141a97d8e52e0883b14fd3e1f4574a05ea
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43879314"
---
# <a name="collect-ink"></a><span data-ttu-id="be292-102">Mürekkep toplama</span><span class="sxs-lookup"><span data-stu-id="be292-102">Collect Ink</span></span>

<span data-ttu-id="be292-103">[Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform dijital mürekkep işlevselliğini önemli bir parçası toplar.</span><span class="sxs-lookup"><span data-stu-id="be292-103">The [Windows Presentation Foundation](../../../../docs/framework/wpf/index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="be292-104">Bu konu, Windows Presentation Foundation (WPF) mürekkep koleksiyonu için yöntemleri açıklar.</span><span class="sxs-lookup"><span data-stu-id="be292-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="be292-105">Önkoşullar</span><span class="sxs-lookup"><span data-stu-id="be292-105">Prerequisites</span></span>

<span data-ttu-id="be292-106">Aşağıdaki örnekleri kullanmak için önce Visual Studio yüklemeniz gerekir ve [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span><span class="sxs-lookup"><span data-stu-id="be292-106">To use the following examples, you must first install Visual Studio and the [!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)].</span></span> <span data-ttu-id="be292-107">WPF uygulamaları yazmak nasıl de anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="be292-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="be292-108">WPF ile çalışmaya başlama hakkında daha fazla bilgi için bkz. [izlenecek yol: ilk WPF Masaüstü Uygulamam](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span><span class="sxs-lookup"><span data-stu-id="be292-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="be292-109">InkCanvas öğesi kullanma</span><span class="sxs-lookup"><span data-stu-id="be292-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="be292-110"><xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> Öğesi mürekkep ' WPF'de toplamak için kolay bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="be292-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="be292-111">Kullanım bir <xref:System.Windows.Controls.InkCanvas> mürekkep girişi almak ve görüntülemek için öğesi.</span><span class="sxs-lookup"><span data-stu-id="be292-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="be292-112">Mürekkep vuruşlarını üretmek için dönüştürücü ile etkileşime giren bir ekran kalemi genelindeki mürekkep yaygın olarak girdiğiniz.</span><span class="sxs-lookup"><span data-stu-id="be292-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="be292-113">Ayrıca, fare, ekran kalemi yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="be292-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="be292-114">Oluşturulan vuruşlar olarak temsil edilmektedir <xref:System.Windows.Ink.Stroke> nesneleri ve programlı ve kullanıcı tarafından giriş yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="be292-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="be292-115"><xref:System.Windows.Controls.InkCanvas> Seçin, değiştirmek veya mevcut bir silme olanağı sağlayan <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="be292-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="be292-116">XAML kullanarak mürekkep koleksiyonunu ekleme gibi kolayca ayarlayabileceğiniz bir **InkCanvas** ağacınıza öğesi.</span><span class="sxs-lookup"><span data-stu-id="be292-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="be292-117">Aşağıdaki örnek ekler bir <xref:System.Windows.Controls.InkCanvas> Visual Studio'da oluşturulan bir varsayılan WPF projesi:</span><span class="sxs-lookup"><span data-stu-id="be292-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="be292-118">**InkCanvas** öğesi mürekkep ek açıklama özellikleri neredeyse tüm XAML öğe türüne eklemenizi olası hale getirerek, alt öğelerini içerebilir.</span><span class="sxs-lookup"><span data-stu-id="be292-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="be292-119">Örneğin, bir metin öğesine mürekkep özelliklerini eklemek için yalnızca bir alt öğesi kolaylaştırır bir <xref:System.Windows.Controls.InkCanvas>:</span><span class="sxs-lookup"><span data-stu-id="be292-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="be292-120">Mürekkep ile görüntü işaretleme desteği eklemek oldukça kolaydır:</span><span class="sxs-lookup"><span data-stu-id="be292-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="be292-121">InkCollection Modları</span><span class="sxs-lookup"><span data-stu-id="be292-121">InkCollection Modes</span></span>

<span data-ttu-id="be292-122"><xref:System.Windows.Controls.InkCanvas> Aracılığıyla çeşitli giriş modları için destek sağlar, <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="be292-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="be292-123">Mürekkep işleme</span><span class="sxs-lookup"><span data-stu-id="be292-123">Manipulate Ink</span></span>

<span data-ttu-id="be292-124"><xref:System.Windows.Controls.InkCanvas> Birçok mürekkep düzenleme işlemleri için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="be292-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="be292-125">Örneğin, <xref:System.Windows.Controls.InkCanvas> destekler arka-ın-kalem siler ve hiçbir ek kod öğesine işlevselliği eklemek için gereklidir.</span><span class="sxs-lookup"><span data-stu-id="be292-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="be292-126">Seçim</span><span class="sxs-lookup"><span data-stu-id="be292-126">Selection</span></span>

<span data-ttu-id="be292-127">Seçim modunu ayarlama ayarı olarak basit <xref:System.Windows.Controls.InkCanvasEditingMode> özelliğini **seçin**.</span><span class="sxs-lookup"><span data-stu-id="be292-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="be292-128">Aşağıdaki kod düzenleme moduna değerine göre ayarlar bir <xref:System.Windows.Forms.CheckBox>:</span><span class="sxs-lookup"><span data-stu-id="be292-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="be292-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="be292-129">DrawingAttributes</span></span>

<span data-ttu-id="be292-130">Kullanım <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> mürekkep vuruşlarını görünümünü değiştirmek için özellik.</span><span class="sxs-lookup"><span data-stu-id="be292-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="be292-131">Örneğin, <xref:System.Windows.Ink.DrawingAttributes.Color%2A> üyesi <xref:System.Windows.Ink.DrawingAttributes> işlenen rengini ayarlar <xref:System.Windows.Ink.Stroke>.</span><span class="sxs-lookup"><span data-stu-id="be292-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="be292-132">Aşağıdaki örnek, seçili vuruşların rengini kırmızı değiştirir:</span><span class="sxs-lookup"><span data-stu-id="be292-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="be292-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="be292-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="be292-134"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> Özelliği, yükseklik, genişlik ve oluşturulması için vuruşlarının rengi gibi özelliklere erişim sağlar bir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="be292-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="be292-135">Siz değiştirdikten sonra <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, girilen tüm gelecek vuruşlar <xref:System.Windows.Controls.InkCanvas> yeni özellik değerleri ile işlenir.</span><span class="sxs-lookup"><span data-stu-id="be292-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="be292-136">Değiştirme yanı sıra <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> arka plan kod dosyasında belirtmek için XAML söz dizimi kullanabilirsiniz <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri.</span><span class="sxs-lookup"><span data-stu-id="be292-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="be292-137">Sonraki örnekte nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.Ink.DrawingAttributes.Color%2A> özelliği.</span><span class="sxs-lookup"><span data-stu-id="be292-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="be292-138">Bu kodu kullanmak için Visual Studio'da "HelloInkCanvas" adlı yeni bir WPF projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="be292-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="be292-139">Değiştirin *MainWindow.xaml* dosyasındaki kodu aşağıdaki kodla:</span><span class="sxs-lookup"><span data-stu-id="be292-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="be292-140">Ardından, aşağıdaki düğmeyi olay işleyicileri arka plan kod dosyasında, MainWindow sınıfının içine ekleyin:</span><span class="sxs-lookup"><span data-stu-id="be292-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="be292-141">Bu kodu kopyaladıktan sonra basın **F5** hata ayıklayıcıda programı çalıştırmak üzere Visual Studio'da.</span><span class="sxs-lookup"><span data-stu-id="be292-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="be292-142">Bildirim nasıl <xref:System.Windows.Controls.StackPanel> düğmeleri üstüne yerleştirir <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="be292-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="be292-143">Mürekkep düğmelerinin üst çalışırsanız <xref:System.Windows.Controls.InkCanvas> düğmelerin arkasında mürekkebi işler ve toplar.</span><span class="sxs-lookup"><span data-stu-id="be292-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="be292-144">Eşdüzey düğmelerdir olmasıdır <xref:System.Windows.Controls.InkCanvas> aksine alt öğeleri.</span><span class="sxs-lookup"><span data-stu-id="be292-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="be292-145">Ayrıca, mürekkep arkasına işlenebilmesi düğmeleri z düzeninde daha yüksektir.</span><span class="sxs-lookup"><span data-stu-id="be292-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="be292-146">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="be292-146">See Also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>