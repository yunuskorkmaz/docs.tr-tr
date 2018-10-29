---
title: Otomatik Düzen Kullanımına Genel Bakış
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: d6ed0da9be32a4a4de4111acfb2d347b7bd5096d
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201562"
---
# <a name="use-automatic-layout-overview"></a><span data-ttu-id="a2565-102">Otomatik Düzen Kullanımına Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="a2565-102">Use Automatic Layout Overview</span></span>
<span data-ttu-id="a2565-103">Bu konu nasıl yazılacağı konusunda geliştiriciler için yönergeler tanıtır [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] yerelleştirilebilir uygulamalarla [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2565-103">This topic introduces guidelines for developers on how to write [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] applications with localizable [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)].</span></span> <span data-ttu-id="a2565-104">Geçmişte, zaman alıcı bir işlem bir kullanıcı Arabirimi yerelleştirmesi oluştu.</span><span class="sxs-lookup"><span data-stu-id="a2565-104">In the past, localization of a UI was a time consuming process.</span></span> <span data-ttu-id="a2565-105">Kullanıcı Arabirimi için uyarlandığı her bir dilin piksel piksel ayarlama gereklidir.</span><span class="sxs-lookup"><span data-stu-id="a2565-105">Each language that the UI was adapted for required a pixel by pixel adjustment.</span></span> <span data-ttu-id="a2565-106">Doğru tasarıma ve doğru kodlama standartları ile Bugün [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] yerelleştiriciler yeniden boyutlandırma ve yeniden konumlandırma yapmak için daha az olması oluşturulabilir.</span><span class="sxs-lookup"><span data-stu-id="a2565-106">Today with the right design and right coding standards, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] can be constructed so that localizers have less resizing and repositioning to do.</span></span> <span data-ttu-id="a2565-107">Daha kolay yeniden boyutlandırılan ve konumlandırılabilir uygulamalar yazma yaklaşım otomatik düzen olarak adlandırılır ve kullanarak gerçekleştirilebilir [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulama tasarım.</span><span class="sxs-lookup"><span data-stu-id="a2565-107">The approach to writing applications that can be more easily resized and repositioned is called automatic layout, and can be achieved by using [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application design.</span></span>  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a><span data-ttu-id="a2565-108">Otomatik Düzen kullanmanın avantajları</span><span class="sxs-lookup"><span data-stu-id="a2565-108">Advantages of Using Automatic Layout</span></span>  
 <span data-ttu-id="a2565-109">Çünkü [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Sunumda güçlü ve esnek, farklı dillerde gereksinimlerine uyacak şekilde ayarlanmış bir uygulamada düzen öğelerini olanağı sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2565-109">Because the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] presentation system is powerful and flexible, it provides the ability to layout elements in an application that can be adjusted to fit the requirements of different languages.</span></span> <span data-ttu-id="a2565-110">Aşağıdaki liste bazı otomatik düzen avantajları işaret eder.</span><span class="sxs-lookup"><span data-stu-id="a2565-110">The following list points out some of the advantages of automatic layout.</span></span>  

-   <span data-ttu-id="a2565-111">Kullanıcı Arabirimi, herhangi bir dilde de görüntüler.</span><span class="sxs-lookup"><span data-stu-id="a2565-111">UI displays well  in any language.</span></span>  

-   <span data-ttu-id="a2565-112">Metin çevrildikten sonra konumunu ve boyutunu denetimleri yeniden ayarlama gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="a2565-112">Reduces the need to readjust position and size of controls after text is translated.</span></span>  
  
-   <span data-ttu-id="a2565-113">Pencere boyutu yeniden ayarlama gereksinimini azaltır.</span><span class="sxs-lookup"><span data-stu-id="a2565-113">Reduces the need to readjust window size.</span></span>  

-   <span data-ttu-id="a2565-114">UI düzeni, herhangi bir dilde düzgün bir şekilde işler.</span><span class="sxs-lookup"><span data-stu-id="a2565-114">UI layout renders properly in any language.</span></span>  

-   <span data-ttu-id="a2565-115">Yerelleştirme, dize çevirisinden biraz daha fazla noktasına azaltılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2565-115">Localization can be reduced to the point that it is little more than string translation.</span></span>  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a><span data-ttu-id="a2565-116">Otomatik Düzen ve denetimler</span><span class="sxs-lookup"><span data-stu-id="a2565-116">Automatic Layout and Controls</span></span>  
 <span data-ttu-id="a2565-117">Otomatik Düzen bir denetimin boyutunu otomatik olarak ayarlamasına olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2565-117">Automatic layout enables an application to adjust the size of a control automatically.</span></span> <span data-ttu-id="a2565-118">Örneğin, bir denetimi, bir dizenin uzunluğunu uyum sağlayacak şekilde değiştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a2565-118">For example, a control can change to accommodate the length of a string.</span></span> <span data-ttu-id="a2565-119">Bu özellik, dize çevrilecek yerelleştiriciler sağlar; Bunlar artık çevrilmiş metin sığdırmak için yeniden boyutlandırma gerekir.</span><span class="sxs-lookup"><span data-stu-id="a2565-119">This capability enables  localizers to translate the string; they no longer need to resize the control to fit the translated text.</span></span> <span data-ttu-id="a2565-120">Aşağıdaki örnek, bir düğme ile İngilizce içeriği oluşturur.</span><span class="sxs-lookup"><span data-stu-id="a2565-120">The following example creates a button with English content.</span></span>  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a2565-121">Örnekte, İspanyolca bir düğme oluşturmak için yapmanız gereken tek şey metni değiştirme.</span><span class="sxs-lookup"><span data-stu-id="a2565-121">In the example, all you have to do to make a Spanish button is change the text.</span></span> <span data-ttu-id="a2565-122">Örneğin,</span><span class="sxs-lookup"><span data-stu-id="a2565-122">For example,</span></span>  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a2565-123">Aşağıdaki grafikte, kod örnekleri çıktısını gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2565-123">The following graphic shows the output of the code samples.</span></span>  
  
 <span data-ttu-id="a2565-124">![Farklı dillerde aynı düğmenin](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span><span class="sxs-lookup"><span data-stu-id="a2565-124">![The same button with text in different languages](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")</span></span>  
<span data-ttu-id="a2565-125">Otomatik yeniden boyutlandırılabilir düğmesi</span><span class="sxs-lookup"><span data-stu-id="a2565-125">Auto Resizable Button</span></span>  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a><span data-ttu-id="a2565-126">Otomatik Düzen ve kodlama standartları</span><span class="sxs-lookup"><span data-stu-id="a2565-126">Automatic Layout and Coding Standards</span></span>  
 <span data-ttu-id="a2565-127">Otomatik düzen yaklaşımı kullanarak, kodlama ve tasarım standartlar ve tam olarak yerelleştirilebilir UI üretmek için kurallar kümesi gerektirir.</span><span class="sxs-lookup"><span data-stu-id="a2565-127">Using the automatic layout approach requires a set of coding and design standards and rules to produce a fully localizable UI.</span></span> <span data-ttu-id="a2565-128">Aşağıdaki yönergeler, kodlamanızı otomatik düzen yardımcı olur.</span><span class="sxs-lookup"><span data-stu-id="a2565-128">The following guidelines will aid your automatic layout coding.</span></span>  

<span data-ttu-id="a2565-129">**Mutlak Konumlar kullanmayın**</span><span class="sxs-lookup"><span data-stu-id="a2565-129">**Do not use absolute positions**</span></span>

- <span data-ttu-id="a2565-130">Kullanmayın <xref:System.Windows.Controls.Canvas> çünkü öğeleri mutlak konumlandırır.</span><span class="sxs-lookup"><span data-stu-id="a2565-130">Do not use <xref:System.Windows.Controls.Canvas> because it positions elements absolutely.</span></span>

- <span data-ttu-id="a2565-131">Kullanım <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, ve <xref:System.Windows.Controls.Grid> denetimleri konumlandırmak için.</span><span class="sxs-lookup"><span data-stu-id="a2565-131">Use <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, and <xref:System.Windows.Controls.Grid> to position controls.</span></span>

<span data-ttu-id="a2565-132">Çeşitli türlerde panolar hakkında bir tartışma için bkz. [panellere genel bakış](../../../../docs/framework/wpf/controls/panels-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a2565-132">For a discussion about various types of panels, see [Panels Overview](../../../../docs/framework/wpf/controls/panels-overview.md).</span></span>

<span data-ttu-id="a2565-133">**Bir pencere için sabit bir boyuta ayarlı değil**</span><span class="sxs-lookup"><span data-stu-id="a2565-133">**Do not set a fixed size for a window**</span></span>

- <span data-ttu-id="a2565-134">Kullanım <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a2565-134">Use <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a2565-135">Örneğin:</span><span class="sxs-lookup"><span data-stu-id="a2565-135">For example:</span></span>

   [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

<span data-ttu-id="a2565-136">**Ekleme bir <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span><span class="sxs-lookup"><span data-stu-id="a2565-136">**Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A>**</span></span>

- <span data-ttu-id="a2565-137">Ekleme bir <xref:System.Windows.FrameworkElement.FlowDirection%2A> uygulamanızın kök öğesine.</span><span class="sxs-lookup"><span data-stu-id="a2565-137">Add a <xref:System.Windows.FrameworkElement.FlowDirection%2A> to the root element of your application.</span></span>

   <span data-ttu-id="a2565-138">WPF yatay desteklemek için kullanışlı bir yol, çift yönlü ve dikey düzeni sağlar.</span><span class="sxs-lookup"><span data-stu-id="a2565-138">WPF provides a convenient way to support horizontal, bidirectional, and vertical layouts.</span></span> <span data-ttu-id="a2565-139">Sunum çerçevesinde <xref:System.Windows.FrameworkElement.FlowDirection%2A> özelliği düzeni tanımlamak için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="a2565-139">In presentation framework, the <xref:System.Windows.FrameworkElement.FlowDirection%2A> property can be used to define layout.</span></span> <span data-ttu-id="a2565-140">Akış yönü modelleri şunlardır:</span><span class="sxs-lookup"><span data-stu-id="a2565-140">The flow-direction patterns are:</span></span>
   
     - <span data-ttu-id="a2565-141"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — Latin, Doğu Asya ve benzeri için yatay düzeni.</span><span class="sxs-lookup"><span data-stu-id="a2565-141"><xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) — horizontal layout for Latin, East Asian, and so forth.</span></span>
     
     - <span data-ttu-id="a2565-142"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb): Arapça, İbranice ve benzeri için çift yönlü.</span><span class="sxs-lookup"><span data-stu-id="a2565-142"><xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) — bidirectional for Arabic, Hebrew, and so forth.</span></span>

<span data-ttu-id="a2565-143">**Bileşik yazı tipleri yerine fiziksel yazı tiplerini kullanma**</span><span class="sxs-lookup"><span data-stu-id="a2565-143">**Use composite fonts instead of physical fonts**</span></span>

- <span data-ttu-id="a2565-144">Bileşik yazı tipleriyle <xref:System.Windows.Controls.Control.FontFamily%2A> özelliği yerelleştirilmiş gerekmez.</span><span class="sxs-lookup"><span data-stu-id="a2565-144">With composite fonts, the <xref:System.Windows.Controls.Control.FontFamily%2A> property does not need to be localized.</span></span>

- <span data-ttu-id="a2565-145">Geliştiriciler, aşağıdaki yazı tipleri kullanın veya kendi oluşturun.</span><span class="sxs-lookup"><span data-stu-id="a2565-145">Developers can use one of the following fonts or create their own.</span></span>

   - <span data-ttu-id="a2565-146">Genel kullanıcı arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2565-146">Global User Interface</span></span>
   - <span data-ttu-id="a2565-147">Genel San Serif</span><span class="sxs-lookup"><span data-stu-id="a2565-147">Global San Serif</span></span>
   - <span data-ttu-id="a2565-148">Genel Serif</span><span class="sxs-lookup"><span data-stu-id="a2565-148">Global Serif</span></span>

<span data-ttu-id="a2565-149">**XML: lang Ekle**</span><span class="sxs-lookup"><span data-stu-id="a2565-149">**Add xml:lang**</span></span>

- <span data-ttu-id="a2565-150">Ekleme `xml:lang` Kullanıcı Arabiriminizin kök öğesi gibi öznitelik `xml:lang="en-US"` İngilizce bir uygulama için.</span><span class="sxs-lookup"><span data-stu-id="a2565-150">Add the `xml:lang` attribute in the root element of your UI, such as `xml:lang="en-US"` for an English application.</span></span>

- <span data-ttu-id="a2565-151">Bileşik yazı tipleri kullandığından `xml:lang` hangi yazı tipinin kullanılacağını belirlemek için çok dilli senaryoları desteklemek için bu özelliği ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="a2565-151">Because composite fonts use `xml:lang` to determine what font to use, set this property to support multilingual scenarios.</span></span>

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a><span data-ttu-id="a2565-152">Otomatik Düzen ve Kılavuzlar</span><span class="sxs-lookup"><span data-stu-id="a2565-152">Automatic Layout and Grids</span></span>  
 <span data-ttu-id="a2565-153"><xref:System.Windows.Controls.Grid> Öğeleri konumlandırmak bir geliştirici sağladığından öğesi, otomatik düzen için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2565-153">The <xref:System.Windows.Controls.Grid> element, is useful for automatic layout because it enables a developer to position elements.</span></span> <span data-ttu-id="a2565-154">A <xref:System.Windows.Controls.Grid> denetimidir kullanılabilir alan bir sütun ve satır düzenlemeyi kullanarak, kendi alt öğeleri arasında dağıtma özelliğine sahiptir.</span><span class="sxs-lookup"><span data-stu-id="a2565-154">A <xref:System.Windows.Controls.Grid> control is capable of distributing the available space among its child elements, using a column and row arrangement.</span></span> <span data-ttu-id="a2565-155">Kullanıcı Arabirimi öğeleri birden çok hücre yayılabilir ve Kılavuzlar Kılavuzlar içinde olması mümkündür.</span><span class="sxs-lookup"><span data-stu-id="a2565-155">The UI elements can span multiple cells, and it is possible to have grids within grids.</span></span> <span data-ttu-id="a2565-156">Kılavuzlar, oluşturmayı ve karmaşık UI konumlandırmayı etkinleştirmek için kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2565-156">Grids are useful because they enable you to create and position complex UI.</span></span> <span data-ttu-id="a2565-157">Aşağıdaki örnek, bazı düğme ve metin konumlandırmak için bir kılavuz kullanmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2565-157">The following example demonstrates using a grid to position some buttons and text.</span></span> <span data-ttu-id="a2565-158">Hücre genişliği ve yüksekliği ayarlandığından bildirimi <xref:System.Windows.GridUnitType.Auto>; bu nedenle, resim sığacak şekilde düğmesi bir görüntü içeren hücreye ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="a2565-158">Notice that the height and width of the cells are set to <xref:System.Windows.GridUnitType.Auto>; therefore, the cell that contains the button with an image adjusts to fit the image.</span></span>  

 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 <span data-ttu-id="a2565-159">Aşağıdaki grafikte önceki kod tarafından üretilen kılavuz gösterir.</span><span class="sxs-lookup"><span data-stu-id="a2565-159">The following graphic shows the grid produced by the previous code.</span></span>  
  
 <span data-ttu-id="a2565-160">![Grid örneği](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span><span class="sxs-lookup"><span data-stu-id="a2565-160">![Grid example](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")</span></span>  
<span data-ttu-id="a2565-161">Kılavuz</span><span class="sxs-lookup"><span data-stu-id="a2565-161">Grid</span></span>  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a><span data-ttu-id="a2565-162">Otomatik Düzen ve Kılavuzlar IsSharedSizeScope özelliğini kullanma</span><span class="sxs-lookup"><span data-stu-id="a2565-162">Automatic Layout and Grids Using the IsSharedSizeScope Property</span></span>  
 <span data-ttu-id="a2565-163">A <xref:System.Windows.Controls.Grid> öğesi, içeriğin sığacağı şekilde ayarlama denetimler oluşturmak için yerelleştirilebilir uygulamalarda kullanışlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2565-163">A <xref:System.Windows.Controls.Grid> element is useful in localizable applications to create controls that adjust to fit content.</span></span> <span data-ttu-id="a2565-164">Ancak, denetimlerin içeriği ne olursa olsun, belirli bir boyutu korumak için istediğiniz zaman zaman.</span><span class="sxs-lookup"><span data-stu-id="a2565-164">However, at times you want controls to maintain a particular size regardless of content.</span></span> <span data-ttu-id="a2565-165">Örneğin, "Tamam" varsa, "İptal" ve "düğmeleri İçeriği sığdırmak için büyük olasılıkla istemezsiniz düğmeleri göz at".</span><span class="sxs-lookup"><span data-stu-id="a2565-165">For example, if you have "OK", "Cancel" and "Browse" buttons you probably do not want the buttons sized to fit the content.</span></span> <span data-ttu-id="a2565-166">Bu durumda <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> ekli özellik aynı boyutlandırma birden çok kılavuz öğesinin arasında paylaşmak için yararlıdır.</span><span class="sxs-lookup"><span data-stu-id="a2565-166">In this case the <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> attached property is useful for sharing the same sizing among multiple grid elements.</span></span> <span data-ttu-id="a2565-167">Aşağıdaki örnek, sütun ve satır boyutlandırma birden çok arasında veri paylaşmayı gösterilmiştir <xref:System.Windows.Controls.Grid> öğeleri.</span><span class="sxs-lookup"><span data-stu-id="a2565-167">The following example demonstrates how to share column and row sizing data between multiple <xref:System.Windows.Controls.Grid> elements.</span></span>  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="a2565-168">**Not** tam kod örneği için bkz. [arasında boyutlandırma özelliklerini Kılavuzlar paylaşımı](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)</span><span class="sxs-lookup"><span data-stu-id="a2565-168">**Note** For the complete code sample, see [Share Sizing Properties Between Grids](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2565-169">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2565-169">See Also</span></span>  
 [<span data-ttu-id="a2565-170">WPF için Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="a2565-170">Globalization for WPF</span></span>](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [<span data-ttu-id="a2565-171">Düğme Oluşturmak için Otomatik Düzeni Kullanma</span><span class="sxs-lookup"><span data-stu-id="a2565-171">Use Automatic Layout to Create a Button</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [<span data-ttu-id="a2565-172">Otomatik Düzen için Kılavuz Kullanma</span><span class="sxs-lookup"><span data-stu-id="a2565-172">Use a Grid for Automatic Layout</span></span>](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
