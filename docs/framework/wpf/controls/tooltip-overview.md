---
title: ToolTip Genel Bakışı
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
ms.openlocfilehash: 0fec31b28a21c2e17986210c852b3d630087842d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181944"
---
# <a name="tooltip-overview"></a><span data-ttu-id="a5fc6-102">ToolTip Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="a5fc6-102">ToolTip Overview</span></span>
<span data-ttu-id="a5fc6-103">Araç ipucu, kullanıcı fare işaretçisini bir öğenin üzerinde duraklattığında görünen küçük bir <xref:System.Windows.Controls.Button>açılır penceredir.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="a5fc6-104">Bu konu araç ucunu tanıtır ve araç ipucu içeriğinin nasıl oluşturulup özelleştirilebildiğini tartışır.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  

<a name="what_is_a_tooltip"></a>
## <a name="what-is-a-tooltip"></a><span data-ttu-id="a5fc6-105">Araç İpucu Nedir?</span><span class="sxs-lookup"><span data-stu-id="a5fc6-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="a5fc6-106">Bir kullanıcı fare işaretçisini araç ipucu olan bir öğenin üzerine taşırsa, araç ipucu içeriği (örneğin, denetimin işlevini açıklayan metin içeriği) içeren bir pencere belirli bir süre için görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="a5fc6-107">Kullanıcı fare işaretçisini denetimden uzağa taşırsa, araç ipucu içeriği netleme alamadığı için pencere kaybolur.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="a5fc6-108">Araç ucunun içeriği bir veya daha fazla metin, resim, şekil veya diğer görsel içerik satırı içerebilir.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="a5fc6-109">Aşağıdaki özelliklerden birini araç ipucu içeriğine ayarlayarak denetim için bir araç ipucu tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="a5fc6-110">Hangi özelliği kullandığınız, araç ucunu tanımlayan denetimin sınıftan <xref:System.Windows.FrameworkContentElement> mı <xref:System.Windows.FrameworkElement> devraldığına bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>
## <a name="creating-a-tooltip"></a><span data-ttu-id="a5fc6-111">Araç İpucu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5fc6-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="a5fc6-112">Aşağıdaki örnekte, bir denetim için <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği bir metin <xref:System.Windows.Controls.Button> dizesine ayarlayarak basit bir araç ipucunasıl oluşturulacak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="a5fc6-113">Araç ucunu <xref:System.Windows.Controls.ToolTip> nesne olarak da tanımlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="a5fc6-114">Aşağıdaki örnek, [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] bir <xref:System.Windows.Controls.ToolTip> öğeyi bir <xref:System.Windows.Controls.TextBox> öğenin araç ucu olarak belirtmek için kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="a5fc6-115">Örneğin <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> özelliği ayarlayarak belirtir unutmayın.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="a5fc6-116">Aşağıdaki örnekte bir <xref:System.Windows.Controls.ToolTip> nesne oluşturmak için kod kullanır.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="a5fc6-117">Örnek a <xref:System.Windows.Controls.ToolTip> oluşturur`tt`( ) ve <xref:System.Windows.Controls.Button>bir ile ilişkilendirer .</span><span class="sxs-lookup"><span data-stu-id="a5fc6-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="a5fc6-118">Ayrıca, araç ipucu içeriğini bir düzen <xref:System.Windows.Controls.ToolTip> öğesine ekleyerek nesne olarak tanımlanmayan araç ipucu <xref:System.Windows.Controls.DockPanel>içeriği de oluşturabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="a5fc6-119">Aşağıdaki örnek, denetimle <xref:System.Windows.FrameworkElement.ToolTip%2A> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Controls.DockPanel> kapatılan bir içeriğe nasıl ayarlanılmayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="a5fc6-120">Araç İpucu ve ToolTipService Sınıflarının Özelliklerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="a5fc6-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="a5fc6-121">Görsel özellikler ayarlayarak ve stilleri uygulayarak araç ipucu içeriğini özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="a5fc6-122">Araç ipucu içeriğini bir <xref:System.Windows.Controls.ToolTip> nesne olarak tanımlarsanız, nesnenin <xref:System.Windows.Controls.ToolTip> görsel özelliklerini ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="a5fc6-123">Aksi takdirde, <xref:System.Windows.Controls.ToolTipService> sınıf üzerinde eşdeğer ekli özellikleri ayarlamanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="a5fc6-124">Özellikleri ve <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> özelliklerini kullanarak araç ipucu içeriğinin konumunu belirtmek için özellikleri nasıl ayarlayalanın bir örneği için, bir Araç İpucu [Konumlandır'a](how-to-position-a-tooltip.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>
## <a name="styling-a-tooltip"></a><span data-ttu-id="a5fc6-125">Araç İpucu Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a5fc6-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="a5fc6-126">Bir özel <xref:System.Windows.Style> <xref:System.Windows.Controls.ToolTip> tanımlayarak a stili yapabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="a5fc6-127">Aşağıdaki <xref:System.Windows.Style> örnek, `Simple` yerleşiminnasıl dengeleneceğini <xref:System.Windows.Controls.ToolTip> gösteren ve <xref:System.Windows.Controls.Control.Background%2A>, , <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>ve <xref:System.Windows.Controls.Control.FontWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="a5fc6-128">ToolTipService'in Zaman Aralığı Özelliklerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="a5fc6-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="a5fc6-129"><xref:System.Windows.Controls.ToolTipService> Sınıf, araç ucu görüntüleme sürelerini ayarlamanız <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>için <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>aşağıdaki <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>özellikleri sağlar: , ve .</span><span class="sxs-lookup"><span data-stu-id="a5fc6-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="a5fc6-130">Bir görünmeden önce <xref:System.Windows.Controls.ToolTip> genellikle kısa bir gecikme belirtmek ve ayrıca ne <xref:System.Windows.Controls.ToolTip> kadar süre görünür kaldığını belirtmek için ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> özellikleri kullanın. <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A></span><span class="sxs-lookup"><span data-stu-id="a5fc6-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="a5fc6-131">Daha fazla bilgi için [bkz: Araç İpucunun Görüntülenmesini Geciktirin.](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a5fc6-131">For more information, see [How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span></span>  
  
 <span data-ttu-id="a5fc6-132">Özellik, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> fare işaretçisini aralarında hızlı bir şekilde hareket ettirdiğinizde, farklı denetimler için araç uçlarının ilk gecikme olmadan görünip görünmeyecektir belirler.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="a5fc6-133"><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Özellik hakkında daha fazla bilgi için Bkz. [BetweenShowDelay Özelliği'ni kullanın.](how-to-use-the-betweenshowdelay-property.md)</span><span class="sxs-lookup"><span data-stu-id="a5fc6-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="a5fc6-134">Aşağıdaki örnekte, bu özelliklerin bir araç ipucu için nasıl ayarlanılabildiğini gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="a5fc6-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a5fc6-135">See also</span></span>

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [<span data-ttu-id="a5fc6-136">Nasıl Dır Konular</span><span class="sxs-lookup"><span data-stu-id="a5fc6-136">How-to Topics</span></span>](tooltip-how-to-topics.md)
