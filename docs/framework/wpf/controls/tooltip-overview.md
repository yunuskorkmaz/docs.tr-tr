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
ms.openlocfilehash: 08b30d8be83ef9d814d17c5d4ec0c95a26bacdad
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790734"
---
# <a name="tooltip-overview"></a><span data-ttu-id="11604-102">ToolTip Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="11604-102">ToolTip Overview</span></span>
<span data-ttu-id="11604-103">Kullanıcı fare işaretçisini bir öğenin üzerinden, gibi üzerinde durakladığında görüntülenen küçük bir açılır pencere bir araç ipucu olan bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="11604-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="11604-104">Bu konu, araç ipucu tanıtır ve oluşturmak ve araç ipucu içeriğini özelleştirmek nasıl açıklar.</span><span class="sxs-lookup"><span data-stu-id="11604-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  

<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="11604-105">Bir araç ipucu nedir?</span><span class="sxs-lookup"><span data-stu-id="11604-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="11604-106">Bir kullanıcı bir araç ipucu sahip bir öğe üzerinde fare işaretçisi hareket ettirdiğinde belirtilen bir zaman miktarı için araç ipucu içeriği (bir denetimin işlevi tanımlayan Örneğin, metin içeriğini) içeren bir pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="11604-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="11604-107">Kullanıcı, fare işaretçisini denetim taşınırsa, araç ipucu içerik odak kazandığı penceresi kaybolur.</span><span class="sxs-lookup"><span data-stu-id="11604-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="11604-108">İçeriği bir araç ipucu, metin, resimler, şekiller veya diğer görsel içerik bir veya daha fazla satır içerebilir.</span><span class="sxs-lookup"><span data-stu-id="11604-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="11604-109">Araç ipucu içeriği ayarlayarak bir denetimin aşağıdaki özelliklerden biri için bir araç ipucu tanımlarsınız.</span><span class="sxs-lookup"><span data-stu-id="11604-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
- <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
- <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="11604-110">Kullandığınız hangi özelliğinin bağlı olup olmadığını tanımlar araç ipucu denetimi devraldığı üzerinde <xref:System.Windows.FrameworkContentElement> veya <xref:System.Windows.FrameworkElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="11604-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="11604-111">Araç ipucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="11604-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="11604-112">Aşağıdaki örnek, basit bir araç ipucu ayarlayarak oluşturma işlemi gösterilmektedir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği için bir <xref:System.Windows.Controls.Button> denetimine bir metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="11604-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="11604-113">Ayrıca, araç ipucu olarak tanımlayabilirsiniz bir <xref:System.Windows.Controls.ToolTip> nesne.</span><span class="sxs-lookup"><span data-stu-id="11604-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="11604-114">Aşağıdaki örnekte [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtmek için bir <xref:System.Windows.Controls.ToolTip> nesnesi araç ipucu olarak bir <xref:System.Windows.Controls.TextBox> öğesi.</span><span class="sxs-lookup"><span data-stu-id="11604-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="11604-115">Örnek belirten Not <xref:System.Windows.Controls.ToolTip> ayarlayarak <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="11604-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="11604-116">Aşağıdaki örnek kod üretmek için kullanır. bir <xref:System.Windows.Controls.ToolTip> nesne.</span><span class="sxs-lookup"><span data-stu-id="11604-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="11604-117">Örnek bir <xref:System.Windows.Controls.ToolTip> (`tt`) ve onunla ilişkilendirir bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="11604-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="11604-118">Tanımlanmamış araç ipucu içeriği de oluşturabileceğiniz bir <xref:System.Windows.Controls.ToolTip> araç ipucu içeriği gibi bir düzen öğesi içinde kapsayan nesne bir <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="11604-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="11604-119">Aşağıdaki örnek nasıl ayarlanacağını gösterir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği bir <xref:System.Windows.Controls.TextBox> sınırlanan içerik için bir <xref:System.Windows.Controls.DockPanel> denetimi.</span><span class="sxs-lookup"><span data-stu-id="11604-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="11604-120">Araç ipucu ve araç ipucu servisi sınıflarının özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="11604-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="11604-121">Araç ipucu içeriği, görsel özelliklerini ayarlamaktan ve stilleri uygulayarak özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="11604-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="11604-122">Araç İpucu olarak içerik tanımlarsanız bir <xref:System.Windows.Controls.ToolTip> nesne görsel özelliklerini ayarlayabileceğiniz <xref:System.Windows.Controls.ToolTip> nesne.</span><span class="sxs-lookup"><span data-stu-id="11604-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="11604-123">Aksi takdirde, üzerinde eşdeğer iliştirilmiş özellikler ayarlamalısınız <xref:System.Windows.Controls.ToolTipService> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="11604-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="11604-124">Kullanarak araç ipucu içeriğinin konumunu belirtmek için özellikleri ayarlama örneği için <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> özellikleri görmek [ToolTip konumlandırma](how-to-position-a-tooltip.md).</span><span class="sxs-lookup"><span data-stu-id="11604-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="11604-125">Bir araç ipucu stil oluşturma</span><span class="sxs-lookup"><span data-stu-id="11604-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="11604-126">Stil uygulayabilirsiniz bir <xref:System.Windows.Controls.ToolTip> özel tanımlayarak <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="11604-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="11604-127">Aşağıdaki örnekte tanımlayan bir <xref:System.Windows.Style> adlı `Simple` nasıl yerleşimini uzaklığı gösteren <xref:System.Windows.Controls.ToolTip> ve ayarlayarak görünümünü değiştirmek <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, ve <xref:System.Windows.Controls.Control.FontWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="11604-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="11604-128">Araç İpucu servisinin zaman aralığı özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="11604-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="11604-129"><xref:System.Windows.Controls.ToolTipService> Sınıfı görüntüleme zamanlarını araç ipucu ayarlamak aşağıdaki özellikleri sağlar: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span><span class="sxs-lookup"><span data-stu-id="11604-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="11604-130">Kullanım <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> bir gecikme belirtmek için özellikleri önce genellikle kısa bir <xref:System.Windows.Controls.ToolTip> görünür ve ayrıca ne kadar süreyle belirtmek için bir <xref:System.Windows.Controls.ToolTip> görünür kalır.</span><span class="sxs-lookup"><span data-stu-id="11604-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="11604-131">Daha fazla bilgi için [nasıl yapılır: Bir araç ipucu görüntülenmesini geciktirme](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="11604-131">For more information, see [How to: Delay the Display of a ToolTip](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms747264(v=vs.90)).</span></span>  
  
 <span data-ttu-id="11604-132"><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Özelliği, farklı denetimler için araç ipuçları, fare işaretçisini hızlı bir şekilde bunlar arasında taşıdığınızda ilk bir gecikme olmadan görüntülenip görüntülenmediğine belirler.</span><span class="sxs-lookup"><span data-stu-id="11604-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="11604-133">Hakkında daha fazla bilgi için <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> özelliğine bakın [BetweenShowDelay özelliğini kullanma](how-to-use-the-betweenshowdelay-property.md).</span><span class="sxs-lookup"><span data-stu-id="11604-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="11604-134">Aşağıdaki örnek, bir araç ipucu için bu özelliklerin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="11604-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="11604-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="11604-135">See also</span></span>

- <xref:System.Windows.Controls.ToolTipService>
- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipEventArgs>
- <xref:System.Windows.Controls.ToolTipEventHandler>
- [<span data-ttu-id="11604-136">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="11604-136">How-to Topics</span></span>](tooltip-how-to-topics.md)
