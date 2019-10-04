---
title: Otomatik Düzen Kullanımına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 0253c57f080705b648d9f416368d0fe974ac83ab
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834664"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="033e9-102">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="033e9-102">Use Automatic Layout Overview</span></span>

<span data-ttu-id="033e9-103">Bu konu, yerelleştirilebilir [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)] ile [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulamalarının nasıl yazılacağı konusunda geliştiriciler için yönergeler tanıtır.</span><span class="sxs-lookup"><span data-stu-id="033e9-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="033e9-104">Geçmişte, bir kullanıcı arabiriminin yerelleştirilmesi zaman alan bir işlemdir.</span><span class="sxs-lookup"><span data-stu-id="033e9-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="033e9-105">Kullanıcı arabiriminin uyarlandığı her dil piksel ayarı için gereken bir piksel.</span><span class="sxs-lookup"><span data-stu-id="033e9-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="033e9-106">Günümüzde, doğru tasarım ve doğru kodlama standartlarıyla [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)], Yerellerle yeniden boyutlandırılması ve bunu yeniden konumlandırılması için oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="033e9-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="033e9-107">Daha kolay yeniden boyutlandırılabilir ve yeniden konumlandırılabilir uygulamaları yazma yaklaşımına otomatik düzen denir ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama tasarımı kullanılarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="033e9-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>

<a name="advantages_of_autolayout"></a>

## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="033e9-108">Otomatik düzen kullanmanın avantajları</span><span class="sxs-lookup"><span data-stu-id="033e9-108">Advantages of Using Automatic Layout</span></span>

<span data-ttu-id="033e9-109">@No__t-0 sunum sistemi güçlü ve esnek olduğundan, bir uygulamadaki öğeleri farklı dillerin gereksinimlerine uyacak şekilde ayarlayabilme yeteneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="033e9-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="033e9-110">Aşağıdaki liste otomatik düzenin avantajlarından bazılarını gösterir.</span><span class="sxs-lookup"><span data-stu-id="033e9-110">The following list points out some of the advantages of automatic layout.</span></span>

- <span data-ttu-id="033e9-111">UI tüm dillerde iyi görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="033e9-111">UI displays well  in any language.</span></span>

- <span data-ttu-id="033e9-112">Metin çevrildikten sonra denetimlerin yalnızca konumunu ve boyutunu ayarlama gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="033e9-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>

- <span data-ttu-id="033e9-113">Yalnızca pencere boyutunu ayarlama gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="033e9-113">Reduces the need to readjust window size.</span></span>

- <span data-ttu-id="033e9-114">Kullanıcı arabirimi düzeni herhangi bir dilde düzgün şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="033e9-114">UI layout renders properly in any language.</span></span>

- <span data-ttu-id="033e9-115">Yerelleştirme, dize çevirinden çok daha fazla olduğu noktaya azaltılabilir.</span><span class="sxs-lookup"><span data-stu-id="033e9-115">Localization can be reduced to the point that it is little more than string translation.</span></span>

<a name="autolayout_controls"></a>

## <a name="automatic-layout-and-controls"></a><span data-ttu-id="033e9-116">Otomatik düzen ve denetimler</span><span class="sxs-lookup"><span data-stu-id="033e9-116">Automatic Layout and Controls</span></span>

<span data-ttu-id="033e9-117">Otomatik düzen, bir uygulamanın bir denetimin boyutunu otomatik olarak ayarlamasını sağlar.</span><span class="sxs-lookup"><span data-stu-id="033e9-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="033e9-118">Örneğin, bir denetim bir dizenin uzunluğuna uyum sağlayacak şekilde değişebilir.</span><span class="sxs-lookup"><span data-stu-id="033e9-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="033e9-119">Bu özellik, Yerelleştiricilerin dizeyi çevirmesini sağlar; Artık, çevrilmiş metne sığacak şekilde denetimi yeniden boyutlandırmaları gerekmez.</span><span class="sxs-lookup"><span data-stu-id="033e9-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="033e9-120">Aşağıdaki örnek, Ingilizce içerikli bir düğme oluşturur.</span><span class="sxs-lookup"><span data-stu-id="033e9-120">The following example creates a button with English content.</span></span>

[!code-xaml[LocalizationBtn_snip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]

<span data-ttu-id="033e9-121">Örnekte, bir Ispanyolca düğme yapmak için yapmanız gerekir, metni değiştirir.</span><span class="sxs-lookup"><span data-stu-id="033e9-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="033e9-122">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="033e9-122">For example,</span></span>

[!code-xaml[LocalizationBtn#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]

<span data-ttu-id="033e9-123">Aşağıdaki grafik kod örneklerinin çıkışını gösterir:</span><span class="sxs-lookup"><span data-stu-id="033e9-123">The following graphic shows the output of the code samples:</span></span>

![Farklı dillerdeki metinle aynı düğme](./media/use-automatic-layout-overview/auto-resizable-button.png)

<a name="autolayout_coding"></a>

## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="033e9-125">Otomatik düzen ve kodlama standartları</span><span class="sxs-lookup"><span data-stu-id="033e9-125">Automatic Layout and Coding Standards</span></span>

<span data-ttu-id="033e9-126">Otomatik düzen yaklaşımını kullanmak, tam olarak yerelleştirilebilir bir kullanıcı arabirimi oluşturmak için bir kodlama ve tasarım standartları ve kuralları gerektirir.</span><span class="sxs-lookup"><span data-stu-id="033e9-126">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="033e9-127">Aşağıdaki kılavuzlar otomatik düzen kodlamasına yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="033e9-127">The following guidelines will aid your automatic layout coding.</span></span>

<span data-ttu-id="033e9-128">**Mutlak konumlar kullanmayın**</span><span class="sxs-lookup"><span data-stu-id="033e9-128">**Do not use absolute positions**</span></span>

- <span data-ttu-id="033e9-129">Öğeleri kesinlikle konumlandırdığından <xref:System.Windows.Controls.Canvas> kullanmayın.</span><span class="sxs-lookup"><span data-stu-id="033e9-129">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="033e9-130">Denetimleri konumlandırmak için <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel> ve <xref:System.Windows.Controls.Grid> kullanın.</span><span class="sxs-lookup"><span data-stu-id="033e9-130">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="033e9-131">Çeşitli panel türleri hakkında bir tartışma için bkz. [panellere genel bakış](../controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="033e9-131">For a discussion about various types of panels, see [Panels Overview](../controls/panels-overview.md).</span></span>

<span data-ttu-id="033e9-132">**Pencere için sabit boyut ayarlamayın**</span><span class="sxs-lookup"><span data-stu-id="033e9-132">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="033e9-133">@No__t-0 kullanın.</span><span class="sxs-lookup"><span data-stu-id="033e9-133">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="033e9-134">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="033e9-134">For example:</span></span>

  [!code-xaml[LocalizationGrid#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="033e9-135">**@No__t ekleyin-1**</span><span class="sxs-lookup"><span data-stu-id="033e9-135">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="033e9-136">Uygulamanızın kök öğesine <xref:System.Windows.FrameworkElement.FlowDirection%2A> ekleyin.</span><span class="sxs-lookup"><span data-stu-id="033e9-136">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

  <span data-ttu-id="033e9-137">WPF, yatay, çift yönlü ve dikey düzenleri desteklemek için kullanışlı bir yol sağlar.</span><span class="sxs-lookup"><span data-stu-id="033e9-137">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="033e9-138">Sunum çerçevesinde <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="033e9-138">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="033e9-139">Akış yönü desenleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="033e9-139">The flow-direction patterns are:</span></span>

  - <span data-ttu-id="033e9-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — Latin, Doğu Asya ve diğerleri için yatay düzen.</span><span class="sxs-lookup"><span data-stu-id="033e9-140"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>

  - <span data-ttu-id="033e9-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — Arapça, Ibranice ve diğerleri için çift yönlü.</span><span class="sxs-lookup"><span data-stu-id="033e9-141"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="033e9-142">**Fiziksel yazı tipleri yerine bileşik yazı tiplerini kullanın**</span><span class="sxs-lookup"><span data-stu-id="033e9-142">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="033e9-143">Bileşik yazı tipleriyle <xref:System.Windows.Controls.Control.FontFamily%2A> özelliğinin yerelleştirilmesi gerekmez.</span><span class="sxs-lookup"><span data-stu-id="033e9-143">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="033e9-144">Geliştiriciler aşağıdaki yazı tiplerinden birini kullanabilir veya kendi türlerini oluşturabilir.</span><span class="sxs-lookup"><span data-stu-id="033e9-144">Developers can use one of the following fonts or create their own.</span></span>

  - <span data-ttu-id="033e9-145">Genel Kullanıcı arabirimi</span><span class="sxs-lookup"><span data-stu-id="033e9-145">Global User Interface</span></span>
  - <span data-ttu-id="033e9-146">Global San Serif</span><span class="sxs-lookup"><span data-stu-id="033e9-146">Global San Serif</span></span>
  - <span data-ttu-id="033e9-147">Küresel tırnaklı</span><span class="sxs-lookup"><span data-stu-id="033e9-147">Global Serif</span></span>

<span data-ttu-id="033e9-148">**XML ekle: lang**</span><span class="sxs-lookup"><span data-stu-id="033e9-148">**Add xml:lang**</span></span>

- <span data-ttu-id="033e9-149">@No__t-0 özniteliğini, Kullanıcı arabiriminin kök öğesine (örneğin, Ingilizce bir uygulama için `xml:lang="en-US"`) ekleyin.</span><span class="sxs-lookup"><span data-stu-id="033e9-149">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="033e9-150">Bileşik yazı tiplerinde kullanılacak yazı tipini belirlemek için `xml:lang` kullanıldığından, bu özelliği çok dilli senaryoları destekleyecek şekilde ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="033e9-150">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>

## <a name="automatic-layout-and-grids"></a><span data-ttu-id="033e9-151">Otomatik düzen ve Izgaralar</span><span class="sxs-lookup"><span data-stu-id="033e9-151">Automatic Layout and Grids</span></span>

<span data-ttu-id="033e9-152">@No__t-0 öğesi, bir geliştiricinin öğeleri konumlandırmalarını sağladığından otomatik düzen için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="033e9-152">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="033e9-153">@No__t-0 denetimi, bir sütun ve satır düzenlemesi kullanarak, alt öğeleri arasında kullanılabilir alanı dağıtabilme özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="033e9-153">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="033e9-154">UI öğeleri birden çok hücreye yayılabilir ve Kılavuzlar içinde ızgaralar olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="033e9-154">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="033e9-155">Kılavuzlar, karmaşık UI oluşturmanıza ve konumlandıramanıza olanak sağladığından faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="033e9-155">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="033e9-156">Aşağıdaki örnek, bazı düğmeleri ve metinleri konumlandırmak için bir kılavuz kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="033e9-156">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="033e9-157">Hücrelerin yüksekliğinin ve genişliğinin <xref:System.Windows.GridUnitType.Auto>; olarak ayarlandığını unutmayın. Bu nedenle, bir görüntüyle birlikte düğme içeren hücre, görüntüye sığacak şekilde ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="033e9-157">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>

[!code-xaml[LocalizationGrid#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]

<span data-ttu-id="033e9-158">Aşağıdaki grafikte, önceki kod tarafından üretilen kılavuz gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="033e9-158">The following graphic shows the grid produced by the previous code.</span></span>

<span data-ttu-id="033e9-159">![Grid örnek](./media/glob-grid.png "glob_grid") Grid</span><span class="sxs-lookup"><span data-stu-id="033e9-159">![Grid example](./media/glob-grid.png "glob_grid") Grid</span></span>

<a name="autolay_grids_issharedsizescope"></a>

## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="033e9-160">IsSharedSizeScope özelliğini kullanarak otomatik düzen ve Izgaralar</span><span class="sxs-lookup"><span data-stu-id="033e9-160">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>

<span data-ttu-id="033e9-161">@No__t-0 öğesi, yerelleştirilebilir uygulamalarda içeriğe uyacak şekilde ayarlanabilecek denetimler oluşturmak için faydalıdır.</span><span class="sxs-lookup"><span data-stu-id="033e9-161">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="033e9-162">Ancak, her zaman, içeriklere bakılmaksızın denetimlerin belirli bir boyutunu korumasını istersiniz.</span><span class="sxs-lookup"><span data-stu-id="033e9-162">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="033e9-163">Örneğin, "Tamam", "Iptal" ve "gözatmaya" düğmeleri varsa, büyük olasılıkla düğmelerin içeriğe sığması için boyutlandırılmayacağını istemezsiniz.</span><span class="sxs-lookup"><span data-stu-id="033e9-163">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="033e9-164">Bu durumda <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> eklenmiş özelliği, birden çok Grid öğesi arasında aynı boyutlandırmayı paylaşmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="033e9-164">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="033e9-165">Aşağıdaki örnek, birden fazla <xref:System.Windows.Controls.Grid> öğesi arasında sütun ve satır boyutlandırma verilerinin nasıl paylaşılacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="033e9-165">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>

[!code-xaml[gridIssharedsizescopeProp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]

> [!NOTE]
> <span data-ttu-id="033e9-166">Tüm kod örneği için bkz. [Kılavuzlar arasında boyutlandırma özelliklerini paylaşma](../controls/how-to-share-sizing-properties-between-grids.md).</span><span class="sxs-lookup"><span data-stu-id="033e9-166">For the complete code sample, see [Share Sizing Properties Between Grids](../controls/how-to-share-sizing-properties-between-grids.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="033e9-167">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="033e9-167">See also</span></span>

- [<span data-ttu-id="033e9-168">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="033e9-168">Globalization for WPF</span></span>](globalization-for-wpf.md)
- [<span data-ttu-id="033e9-169">Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="033e9-169">Use Automatic Layout to Create a Button</span></span>](how-to-use-automatic-layout-to-create-a-button.md)
- [<span data-ttu-id="033e9-170">Otomatik Düzen için Kılavuz Kullanma</span><span class="sxs-lookup"><span data-stu-id="033e9-170">Use a Grid for Automatic Layout</span></span>](how-to-use-a-grid-for-automatic-layout.md)
