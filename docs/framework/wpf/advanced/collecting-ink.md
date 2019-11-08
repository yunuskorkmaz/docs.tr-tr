---
title: WPF uygulamalarında Mürekkep toplama
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
ms.openlocfilehash: 8109e0d6a746d6ca23c25643c510014c1a1e656c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740878"
---
# <a name="collect-ink"></a><span data-ttu-id="a37f2-102">Mürekkep toplama</span><span class="sxs-lookup"><span data-stu-id="a37f2-102">Collect Ink</span></span>

<span data-ttu-id="a37f2-103">[Windows Presentation Foundation](../index.md) platformu, işlevselliğinin temel bir parçası olarak dijital mürekkep toplar.</span><span class="sxs-lookup"><span data-stu-id="a37f2-103">The [Windows Presentation Foundation](../index.md) platform collects digital ink as a core part of its functionality.</span></span> <span data-ttu-id="a37f2-104">Bu konuda Windows Presentation Foundation (WPF) içindeki mürekkep koleksiyonu için yöntemler ele alınmaktadır.</span><span class="sxs-lookup"><span data-stu-id="a37f2-104">This topic discusses methods for collection of ink in Windows Presentation Foundation (WPF).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a37f2-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="a37f2-105">Prerequisites</span></span>

<span data-ttu-id="a37f2-106">Aşağıdaki örnekleri kullanmak için, önce Visual Studio 'Yu ve Windows SDK yüklemeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-106">To use the following examples, you must first install Visual Studio and the Windows SDK.</span></span> <span data-ttu-id="a37f2-107">WPF için nasıl uygulama yazılacağını de anlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-107">You should also understand how to write applications for the WPF.</span></span> <span data-ttu-id="a37f2-108">WPF kullanmaya başlama hakkında daha fazla bilgi için bkz. [Izlenecek yol: Ilk WPF Masaüstü](../getting-started/walkthrough-my-first-wpf-desktop-application.md)Uygulamam.</span><span class="sxs-lookup"><span data-stu-id="a37f2-108">For more information about getting started with WPF, see [Walkthrough: My first WPF desktop application](../getting-started/walkthrough-my-first-wpf-desktop-application.md).</span></span>

## <a name="use-the-inkcanvas-element"></a><span data-ttu-id="a37f2-109">InkCanvas öğesini kullanma</span><span class="sxs-lookup"><span data-stu-id="a37f2-109">Use the InkCanvas Element</span></span>

<span data-ttu-id="a37f2-110"><xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> öğesi WPF 'de mürekkep toplamanın en kolay yolunu sağlar.</span><span class="sxs-lookup"><span data-stu-id="a37f2-110">The <xref:System.Windows.Controls.InkCanvas?displayProperty=fullName> element provides the easiest way to collect ink in WPF.</span></span> <span data-ttu-id="a37f2-111">Mürekkep girişi almak ve göstermek için bir <xref:System.Windows.Controls.InkCanvas> öğesi kullanın.</span><span class="sxs-lookup"><span data-stu-id="a37f2-111">Use an <xref:System.Windows.Controls.InkCanvas> element to receive and display ink input.</span></span> <span data-ttu-id="a37f2-112">Mürekkep vuruşları oluşturmak için bir çizim tablasına etkileşim kuran bir ekran kalemi kullanarak genellikle mürekkep girmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-112">You commonly input ink through the use of a stylus, which interacts with a digitizer to produce ink strokes.</span></span> <span data-ttu-id="a37f2-113">Ayrıca fare, bir ekran kalemi yerine kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-113">In addition, a mouse can be used in place of a stylus.</span></span> <span data-ttu-id="a37f2-114">Oluşturulan konturlar <xref:System.Windows.Ink.Stroke> nesne olarak temsil edilir ve hem programlı olarak hem de Kullanıcı girişi tarafından yönetilebilir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-114">The created strokes are represented as <xref:System.Windows.Ink.Stroke> objects, and they can be manipulated both programmatically and by user input.</span></span> <span data-ttu-id="a37f2-115"><xref:System.Windows.Controls.InkCanvas>, kullanıcıların var olan bir <xref:System.Windows.Ink.Stroke>seçmesini, değiştirmesini veya silmesini sağlar.</span><span class="sxs-lookup"><span data-stu-id="a37f2-115">The <xref:System.Windows.Controls.InkCanvas> enables users to select, modify, or delete an existing <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="a37f2-116">XAML kullanarak, ağaca bir **InkCanvas** öğesi eklemek kadar mürekkep toplamayı kolayca ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a37f2-116">By using XAML, you can set up ink collection as easily as adding an **InkCanvas** element to your tree.</span></span> <span data-ttu-id="a37f2-117">Aşağıdaki örnek, Visual Studio 'da oluşturulan varsayılan WPF projesine bir <xref:System.Windows.Controls.InkCanvas> ekler:</span><span class="sxs-lookup"><span data-stu-id="a37f2-117">The following example adds an <xref:System.Windows.Controls.InkCanvas> to a default WPF project created in Visual Studio:</span></span>

[!code-xaml[DigitalInkTopics#6](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#6)]

<span data-ttu-id="a37f2-118">**InkCanvas** öğesi Ayrıca, daha önce her türlü xaml öğesine mürekkep ek açıklama özellikleri eklemenizi olanaklı hale getiren alt öğeleri de içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-118">The **InkCanvas** element can also contain child elements, making it possible to add ink annotation capabilities to almost any type of XAML element.</span></span> <span data-ttu-id="a37f2-119">Örneğin, bir metin öğesine mürekkep özellikleri eklemek için bunu bir <xref:System.Windows.Controls.InkCanvas>alt öğesi yapmanız yeterlidir:</span><span class="sxs-lookup"><span data-stu-id="a37f2-119">For example, to add inking capabilities to a text element, simply make it a child of an <xref:System.Windows.Controls.InkCanvas>:</span></span>

[!code-xaml[DigitalInkTopics#5](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#5)]

<span data-ttu-id="a37f2-120">Bir görüntüyü mürekkeple işaretlemek için destek eklemek oldukça kolaydır:</span><span class="sxs-lookup"><span data-stu-id="a37f2-120">Adding support for marking up an image with ink is just as easy:</span></span>

[!code-xaml[DigitalInkTopics#7](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window2.xaml#7)]

### <a name="inkcollection-modes"></a><span data-ttu-id="a37f2-121">InkCollection modları</span><span class="sxs-lookup"><span data-stu-id="a37f2-121">InkCollection Modes</span></span>

<span data-ttu-id="a37f2-122"><xref:System.Windows.Controls.InkCanvas>, <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> özelliği aracılığıyla çeşitli giriş modları için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a37f2-122">The <xref:System.Windows.Controls.InkCanvas> provides support for various input modes through its <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> property.</span></span>

### <a name="manipulate-ink"></a><span data-ttu-id="a37f2-123">Mürekkep işleme</span><span class="sxs-lookup"><span data-stu-id="a37f2-123">Manipulate Ink</span></span>

<span data-ttu-id="a37f2-124"><xref:System.Windows.Controls.InkCanvas> birçok mürekkep düzenlemesi işlemi için destek sağlar.</span><span class="sxs-lookup"><span data-stu-id="a37f2-124">The <xref:System.Windows.Controls.InkCanvas> provides support for many ink editing operations.</span></span> <span data-ttu-id="a37f2-125">Örneğin, <xref:System.Windows.Controls.InkCanvas> kalem arka silmeyi destekler ve işlevselliği öğesine eklemek için ek kod gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a37f2-125">For example, <xref:System.Windows.Controls.InkCanvas> supports back-of-pen erase, and no additional code is needed to add the functionality to the element.</span></span>

#### <a name="selection"></a><span data-ttu-id="a37f2-126">Seçim</span><span class="sxs-lookup"><span data-stu-id="a37f2-126">Selection</span></span>

<span data-ttu-id="a37f2-127">Seçim modunu ayarlamak <xref:System.Windows.Controls.InkCanvasEditingMode> özelliğini **Seçilecek**kadar basittir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-127">Setting selection mode is as simple as setting the <xref:System.Windows.Controls.InkCanvasEditingMode> property to **Select**.</span></span>

<span data-ttu-id="a37f2-128">Aşağıdaki kod, bir <xref:System.Windows.Forms.CheckBox>değerine göre, Düzen modunu ayarlar:</span><span class="sxs-lookup"><span data-stu-id="a37f2-128">The following code sets the editing mode based on the value of a <xref:System.Windows.Forms.CheckBox>:</span></span>

[!code-csharp[DigitalInkTopics#8](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#8)]
[!code-vb[DigitalInkTopics#8](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#8)]

#### <a name="drawingattributes"></a><span data-ttu-id="a37f2-129">DrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="a37f2-129">DrawingAttributes</span></span>

<span data-ttu-id="a37f2-130">Mürekkep vuruşlarının görünümünü değiştirmek için <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> özelliğini kullanın.</span><span class="sxs-lookup"><span data-stu-id="a37f2-130">Use the <xref:System.Windows.Ink.Stroke.DrawingAttributes%2A> property to change the appearance of ink strokes.</span></span> <span data-ttu-id="a37f2-131">Örneğin, <xref:System.Windows.Ink.DrawingAttributes> <xref:System.Windows.Ink.DrawingAttributes.Color%2A> üyesi, işlenen <xref:System.Windows.Ink.Stroke>rengini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="a37f2-131">For instance, the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> member of <xref:System.Windows.Ink.DrawingAttributes> sets the color of the rendered <xref:System.Windows.Ink.Stroke>.</span></span>

<span data-ttu-id="a37f2-132">Aşağıdaki örnek, seçili vuruşların rengini kırmızı olarak değiştirir:</span><span class="sxs-lookup"><span data-stu-id="a37f2-132">The following example changes the color of the selected strokes to red:</span></span>

[!code-csharp[DigitalInkTopics#9](~/samples/snippets/csharp/VS_Snippets_Wpf/DigitalInkTopics/CSharp/Window1.xaml.cs#9)]
[!code-vb[DigitalInkTopics#9](~/samples/snippets/visualbasic/VS_Snippets_Wpf/DigitalInkTopics/VisualBasic/Window1.xaml.vb#9)]

### <a name="defaultdrawingattributes"></a><span data-ttu-id="a37f2-133">DefaultDrawingAttributes</span><span class="sxs-lookup"><span data-stu-id="a37f2-133">DefaultDrawingAttributes</span></span>

<span data-ttu-id="a37f2-134"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özelliği, bir <xref:System.Windows.Controls.InkCanvas>oluşturulacak vuruşların yüksekliği, genişliği ve rengi gibi özelliklere erişim sağlar.</span><span class="sxs-lookup"><span data-stu-id="a37f2-134">The <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> property provides access to properties such as the height, width, and color of the strokes to be created in an <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="a37f2-135"><xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>değiştirdikten sonra, <xref:System.Windows.Controls.InkCanvas> girilen tüm gelecek konturlar yeni özellik değerleriyle işlenir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-135">Once you change the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, all future strokes entered into the <xref:System.Windows.Controls.InkCanvas> are rendered with the new property values.</span></span>

<span data-ttu-id="a37f2-136">Arka plan kod dosyasında <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> değiştirmeye ek olarak, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> özellikleri belirtmek için XAML söz dizimini kullanabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a37f2-136">In addition to modifying the <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> in the code-behind file, you can use XAML syntax for specifying <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> properties.</span></span>

<span data-ttu-id="a37f2-137">Sonraki örnekte <xref:System.Windows.Ink.DrawingAttributes.Color%2A> özelliğinin nasıl ayarlanacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-137">The next example demonstrates how to set the <xref:System.Windows.Ink.DrawingAttributes.Color%2A> property.</span></span> <span data-ttu-id="a37f2-138">Bu kodu kullanmak için, Visual Studio 'da "HelloInkCanvas" adlı yeni bir WPF projesi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a37f2-138">To use this code, create a new WPF project called "HelloInkCanvas" in Visual Studio.</span></span> <span data-ttu-id="a37f2-139">*MainWindow. xaml* dosyasındaki kodu aşağıdaki kodla değiştirin:</span><span class="sxs-lookup"><span data-stu-id="a37f2-139">Replace the code in the *MainWindow.xaml* file with the following code:</span></span>

[!code-xaml[HelloInkCanvas#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml#1)]

<span data-ttu-id="a37f2-140">Sonra, MainWindow sınıfının içindeki arka plan kod dosyasına aşağıdaki düğme olay işleyicilerini ekleyin:</span><span class="sxs-lookup"><span data-stu-id="a37f2-140">Next, add the following button event handlers to the code behind file, inside the MainWindow class:</span></span>

[!code-csharp[HelloInkCanvas#2](~/samples/snippets/csharp/VS_Snippets_Wpf/HelloInkCanvas/CSharp/Window1.xaml.cs#2)]

<span data-ttu-id="a37f2-141">Bu kodu kopyaladıktan sonra Visual Studio 'da **F5** ' e basarak programı hata ayıklayıcıda çalıştırın.</span><span class="sxs-lookup"><span data-stu-id="a37f2-141">After copying this code, press **F5** in Visual Studio to run the program in the debugger.</span></span>

<span data-ttu-id="a37f2-142"><xref:System.Windows.Controls.StackPanel> düğmeleri <xref:System.Windows.Controls.InkCanvas>üstüne nasıl yerleştirdiğine dikkat edin.</span><span class="sxs-lookup"><span data-stu-id="a37f2-142">Notice how the <xref:System.Windows.Controls.StackPanel> places the buttons on top of the <xref:System.Windows.Controls.InkCanvas>.</span></span> <span data-ttu-id="a37f2-143">Düğmelerin üst kısmında mürekkebi denemeye çalışırsanız, <xref:System.Windows.Controls.InkCanvas> düğmelerin arkasındaki mürekkebi toplar ve işler.</span><span class="sxs-lookup"><span data-stu-id="a37f2-143">If you try to ink over the top of the buttons, the <xref:System.Windows.Controls.InkCanvas> collects and renders the ink behind the buttons.</span></span> <span data-ttu-id="a37f2-144">Bunun nedeni, alt öğelerin aksine düğmelerin eşdüzey <xref:System.Windows.Controls.InkCanvas>.</span><span class="sxs-lookup"><span data-stu-id="a37f2-144">This is because the buttons are siblings of the <xref:System.Windows.Controls.InkCanvas> as opposed to children.</span></span> <span data-ttu-id="a37f2-145">Ayrıca, düğmeler z düzeninde daha yüksektir, bu nedenle mürekkep bunların arkasında işlenir.</span><span class="sxs-lookup"><span data-stu-id="a37f2-145">Also, the buttons are higher in the z-order, so the ink is rendered behind them.</span></span>

## <a name="see-also"></a><span data-ttu-id="a37f2-146">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a37f2-146">See also</span></span>

- <xref:System.Windows.Ink.DrawingAttributes>
- <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>
- <xref:System.Windows.Ink>
