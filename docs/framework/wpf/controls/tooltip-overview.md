---
title: "ToolTip Genel Bakışı"
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
- ToolTip control [WPF], about ToolTip control
- controls [WPF], ToolTip
ms.assetid: f06c1603-e9cb-4809-8a62-234607fc52f7
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c945d23def3bbf6284e7e0db95d391066256df6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="tooltip-overview"></a><span data-ttu-id="d8922-102">ToolTip Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="d8922-102">ToolTip Overview</span></span>
<span data-ttu-id="d8922-103">Bir kullanıcı bir öğe üzerinde gibi üzerinde fare işaretçisini durduğu zaman görüntülenen küçük bir açılır pencere bir araç ipucu olan bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="d8922-103">A tooltip is a small pop-up window that appears when a user pauses the mouse pointer over an element, such as over a <xref:System.Windows.Controls.Button>.</span></span> <span data-ttu-id="d8922-104">Bu konu, araç ipucu tanıtır ve nasıl oluşturulacağı ve araç ipucu içeriğini özelleştirmek açıklanır.</span><span class="sxs-lookup"><span data-stu-id="d8922-104">This topic introduces the tooltip and discusses how to create and customize tooltip content.</span></span>  
  
 
  
<a name="what_is_a_tooltip"></a>   
## <a name="what-is-a-tooltip"></a><span data-ttu-id="d8922-105">Bir araç ipucu nedir?</span><span class="sxs-lookup"><span data-stu-id="d8922-105">What Is a Tooltip?</span></span>  
 <span data-ttu-id="d8922-106">Bir kullanıcı bir araç ipucu olan bir öğeyi fare işaretçisini geçtiğinde, belirtilen bir süre için araç ipucu içeriği (bir denetim işlevini açıklayan Örneğin, metin içeriği) içeren bir pencere görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="d8922-106">When a user moves the mouse pointer over an element that has a tooltip, a window that contains tooltip content (for example, text content that describes the function of a control) appears for a specified amount of time.</span></span> <span data-ttu-id="d8922-107">Kullanıcı denetimi fare işaretçisini geçerse, araç ipucu içeriği odak aldıklarından pencere kaybolur.</span><span class="sxs-lookup"><span data-stu-id="d8922-107">If the user moves the mouse pointer away from the control, the window disappears because the tooltip content cannot receive focus.</span></span>  
  
 <span data-ttu-id="d8922-108">İçeriği bir araç ipucu, bir veya birkaç satırlık metin, görüntüler, şekiller veya diğer görsel içerik içerebilir.</span><span class="sxs-lookup"><span data-stu-id="d8922-108">The content of a tooltip can contain one or more lines of text, images, shapes, or other visual content.</span></span> <span data-ttu-id="d8922-109">Araç ipucu içeriği ayarlayarak bir denetim aşağıdaki özelliklerden biri için bir araç ipucu tanımlayın.</span><span class="sxs-lookup"><span data-stu-id="d8922-109">You define a tooltip for a control by setting one of the following properties to the tooltip content.</span></span>  
  
-   <xref:System.Windows.FrameworkContentElement.ToolTip%2A?displayProperty=nameWithType>  
  
-   <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType>  
  
 <span data-ttu-id="d8922-110">Hangi özelliği kullandığınız bağlı olup olmadığını tanımlar araç ipucu denetimi devraldığı üzerinde <xref:System.Windows.FrameworkContentElement> veya <xref:System.Windows.FrameworkElement> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d8922-110">Which property you use depends on whether the control that defines the tooltip inherits from the <xref:System.Windows.FrameworkContentElement> or <xref:System.Windows.FrameworkElement> class.</span></span>  
  
<a name="create_tooltip"></a>   
## <a name="creating-a-tooltip"></a><span data-ttu-id="d8922-111">Araç ipucu oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8922-111">Creating a ToolTip</span></span>  
 <span data-ttu-id="d8922-112">Aşağıdaki örnek ayarlayarak basit bir araç ipucu oluşturulacağını gösterir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği için bir <xref:System.Windows.Controls.Button> denetlemek için bir metin dizesi.</span><span class="sxs-lookup"><span data-stu-id="d8922-112">The following example shows how to create a simple tooltip by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A> property for a <xref:System.Windows.Controls.Button> control to a text string.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipstring)]  
  
 <span data-ttu-id="d8922-113">Araç İpucu olarak da tanımlayabilirsiniz bir <xref:System.Windows.Controls.ToolTip> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d8922-113">You can also define a tooltip as a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="d8922-114">Aşağıdaki örnek kullanır [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] belirtmek için bir <xref:System.Windows.Controls.ToolTip> nesnesi araç ipucu olarak bir <xref:System.Windows.Controls.TextBox> öğesi.</span><span class="sxs-lookup"><span data-stu-id="d8922-114">The following example uses [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] to specify a <xref:System.Windows.Controls.ToolTip> object as the tooltip of a <xref:System.Windows.Controls.TextBox> element.</span></span> <span data-ttu-id="d8922-115">Örnek belirtir Not <xref:System.Windows.Controls.ToolTip> ayarlayarak <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> özelliği.</span><span class="sxs-lookup"><span data-stu-id="d8922-115">Note that the example specifies the <xref:System.Windows.Controls.ToolTip> by setting the <xref:System.Windows.FrameworkElement.ToolTip%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-xaml[ToolTipSimple#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#tooltip)]  
  
 <span data-ttu-id="d8922-116">Aşağıdaki örnek kod oluşturmak için kullanılır. bir <xref:System.Windows.Controls.ToolTip> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d8922-116">The following example uses code to generate a <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="d8922-117">Örnekte bir <xref:System.Windows.Controls.ToolTip> (`tt`) ve ile ilişkilendirir bir <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="d8922-117">The example creates a <xref:System.Windows.Controls.ToolTip> (`tt`) and associates it with a <xref:System.Windows.Controls.Button>.</span></span>  
  
 [!code-csharp[ToolTipSimple#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml.cs#2)]
 [!code-vb[ToolTipSimple#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipSimple/VisualBasic/Window1.xaml.vb#2)]  
  
 <span data-ttu-id="d8922-118">Ayrıca olarak tanımlanmamış araç ipucu içeriği oluşturabilirsiniz bir <xref:System.Windows.Controls.ToolTip> gibi bir düzen öğesi içinde araç ipucu içeriği kapsayan nesne bir <xref:System.Windows.Controls.DockPanel>.</span><span class="sxs-lookup"><span data-stu-id="d8922-118">You can also create tooltip content that is not defined as a <xref:System.Windows.Controls.ToolTip> object by enclosing the tooltip content in a layout element, such as a <xref:System.Windows.Controls.DockPanel>.</span></span> <span data-ttu-id="d8922-119">Aşağıdaki örnekte nasıl ayarlanacağını gösterir <xref:System.Windows.FrameworkElement.ToolTip%2A> özelliği bir <xref:System.Windows.Controls.TextBox> sınırlanan içerik için bir <xref:System.Windows.Controls.DockPanel> denetim.</span><span class="sxs-lookup"><span data-stu-id="d8922-119">The following example shows how to set the <xref:System.Windows.FrameworkElement.ToolTip%2A> property of a <xref:System.Windows.Controls.TextBox> to content that is enclosed in a <xref:System.Windows.Controls.DockPanel> control.</span></span>  
  
 [!code-xaml[GroupBoxSnippet#ToolTipDockPanel](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#tooltipdockpanel)]  
  
<a name="Using_the_ToolTip_and_ToolTipService_Properties"></a>   
## <a name="using-the-properties-of-the-tooltip-and-tooltipservice-classes"></a><span data-ttu-id="d8922-120">Araç ipucu ve araç ipucu servisi sınıflarının özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="d8922-120">Using the Properties of the ToolTip and ToolTipService Classes</span></span>  
 <span data-ttu-id="d8922-121">Araç ipucu içeriği görsel özelliklerini ayarlamaktan ve stiller uygulayarak özelleştirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d8922-121">You can customize tooltip content by setting visual properties and applying styles.</span></span> <span data-ttu-id="d8922-122">Araç İpucu olarak içeriği tanımlarsanız bir <xref:System.Windows.Controls.ToolTip> nesne görsel özelliklerini ayarlayabilirsiniz <xref:System.Windows.Controls.ToolTip> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d8922-122">If you define the tooltip content as a <xref:System.Windows.Controls.ToolTip> object, you can set the visual properties of the <xref:System.Windows.Controls.ToolTip> object.</span></span> <span data-ttu-id="d8922-123">Aksi takdirde, eşdeğer ekli özellikler üzerinde ayarlamanız gerekir <xref:System.Windows.Controls.ToolTipService> sınıfı.</span><span class="sxs-lookup"><span data-stu-id="d8922-123">Otherwise, you must set equivalent attached properties on the <xref:System.Windows.Controls.ToolTipService> class.</span></span>  
  
 <span data-ttu-id="d8922-124">Kullanarak araç ipucu içeriğinin konumunu belirtmek için özelliklerini ayarlamak nasıl bir örnek için <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> özellikleri, görmek [bir araç ipucu, konum](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span><span class="sxs-lookup"><span data-stu-id="d8922-124">For an example of how to set properties in order to specify the position of tooltip content by using the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> properties, see [Position a ToolTip](../../../../docs/framework/wpf/controls/how-to-position-a-tooltip.md).</span></span>  
  
<a name="StylingToolTip"></a>   
## <a name="styling-a-tooltip"></a><span data-ttu-id="d8922-125">Bir araç ipucu stil oluşturma</span><span class="sxs-lookup"><span data-stu-id="d8922-125">Styling a ToolTip</span></span>  
 <span data-ttu-id="d8922-126">Stil ekleyebilirsiniz bir <xref:System.Windows.Controls.ToolTip> özel tanımlayarak <xref:System.Windows.Style>.</span><span class="sxs-lookup"><span data-stu-id="d8922-126">You can style a <xref:System.Windows.Controls.ToolTip> by defining a custom <xref:System.Windows.Style>.</span></span> <span data-ttu-id="d8922-127">Aşağıdaki örnek tanımlayan bir <xref:System.Windows.Style> adlı `Simple` nasıl yerleşimini uzaklığı gösterir <xref:System.Windows.Controls.ToolTip> ve ayarlayarak görünümünü değiştirme <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, ve <xref:System.Windows.Controls.Control.FontWeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8922-127">The following example defines a <xref:System.Windows.Style> called `Simple` that shows how to offset the placement of the <xref:System.Windows.Controls.ToolTip> and change its appearance by setting the <xref:System.Windows.Controls.Control.Background%2A>, <xref:System.Windows.Controls.Control.Foreground%2A>, <xref:System.Windows.Controls.Control.FontSize%2A>, and <xref:System.Windows.Controls.Control.FontWeight%2A>.</span></span>  
  
 [!code-xaml[ToolTipSimple#Style](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipSimple/CSharp/Pane1.xaml#style)]  
  
<a name="UsingtheToolTipServiceTimeIntervalProperties"></a>   
## <a name="using-the-time-interval-properties-of-tooltipservice"></a><span data-ttu-id="d8922-128">Araç İpucu servisi zaman aralığı özelliklerini kullanma</span><span class="sxs-lookup"><span data-stu-id="d8922-128">Using the Time Interval Properties of ToolTipService</span></span>  
 <span data-ttu-id="d8922-129"><xref:System.Windows.Controls.ToolTipService> Sınıfı sağlar, araç ipucu ayarlamak aşağıdaki özellikleri görüntüleme zamanlarını: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span><span class="sxs-lookup"><span data-stu-id="d8922-129">The <xref:System.Windows.Controls.ToolTipService> class provides the following properties for you to set tooltip display times: <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A>, <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A>, and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A>.</span></span>  
  
 <span data-ttu-id="d8922-130">Kullanım <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> ve <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> bir gecikme belirtmek için özellikleri önce genellikle kısa bir <xref:System.Windows.Controls.ToolTip> görünür ve ayrıca ne kadar süreyle belirtmek için bir <xref:System.Windows.Controls.ToolTip> görünür kalır.</span><span class="sxs-lookup"><span data-stu-id="d8922-130">Use the <xref:System.Windows.Controls.ToolTipService.InitialShowDelay%2A> and <xref:System.Windows.Controls.ToolTipService.ShowDuration%2A> properties to specify a delay, typically brief, before a <xref:System.Windows.Controls.ToolTip> appears and also to specify how long a <xref:System.Windows.Controls.ToolTip> remains visible.</span></span> <span data-ttu-id="d8922-131">Daha fazla bilgi için bkz: [nasıl yapılır: araç ipucu görüntüsünü gecikme](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span><span class="sxs-lookup"><span data-stu-id="d8922-131">For more information, see [How to: Delay the Display of a ToolTip](http://msdn.microsoft.com/library/618e05ef-f2bf-4a53-a0f4-aacb49918bd7).</span></span>  
  
 <span data-ttu-id="d8922-132"><xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> Özelliği, fare işaretçisini hızla arasında taşıdığınızda farklı denetimler için araç ipuçları ilk gecikme olmadan görünür olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="d8922-132">The <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property determines if tooltips for different controls appear without an initial delay when you move the mouse pointer quickly between them.</span></span> <span data-ttu-id="d8922-133">Hakkında daha fazla bilgi için <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> özelliği, bkz: [BetweenShowDelay özelliğini kullanma](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span><span class="sxs-lookup"><span data-stu-id="d8922-133">For more information about the <xref:System.Windows.Controls.ToolTipService.BetweenShowDelay%2A> property, see [Use the BetweenShowDelay Property](../../../../docs/framework/wpf/controls/how-to-use-the-betweenshowdelay-property.md).</span></span>  
  
 <span data-ttu-id="d8922-134">Aşağıdaki örnek, bir araç ipucu için bu özelliklerin nasıl ayarlanacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="d8922-134">The following example shows how to set these properties for a tooltip.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
## <a name="see-also"></a><span data-ttu-id="d8922-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d8922-135">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTipService>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipEventArgs>  
 <xref:System.Windows.Controls.ToolTipEventHandler>  
 [<span data-ttu-id="d8922-136">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="d8922-136">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)
