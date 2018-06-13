---
title: 'Nasıl yapılır: ToolTip Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 218d8814cf75cd80a63c94397ed00e92c6a9a8fb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555944"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="8ab03-102">Nasıl yapılır: ToolTip Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="8ab03-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="8ab03-103">Bu örnek ekranda araç ipucu konumunu belirtmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="8ab03-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8ab03-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="8ab03-104">Example</span></span>  
 <span data-ttu-id="8ab03-105">İkisi de tanımlanan beş özellikler kümesini kullanarak bir araç ipucu yerleştirebilirsiniz <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="8ab03-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="8ab03-106">Aşağıdaki tabloda bu iki beş özelliklerinin gösterir ve sınıf göre kendi referans belgelerine ait bağlantılar sağlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="8ab03-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="8ab03-107">Karşılık gelen araç ipucu özelliklere göre sınıfı</span><span class="sxs-lookup"><span data-stu-id="8ab03-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="8ab03-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Sınıf özellikleri</span><span class="sxs-lookup"><span data-stu-id="8ab03-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="8ab03-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Sınıf özellikleri</span><span class="sxs-lookup"><span data-stu-id="8ab03-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="8ab03-110">Bir araç ipucu içeriğini kullanarak tanımlarsanız bir <xref:System.Windows.Controls.ToolTip> nesnesi, her iki sınıfın özelliklerini kullanabilirsiniz; ancak, <xref:System.Windows.Controls.ToolTipService> özellikleri daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="8ab03-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="8ab03-111">Kullanım <xref:System.Windows.Controls.ToolTipService> olarak tanımlı değil araç ipuçları için özellikleri <xref:System.Windows.Controls.ToolTip> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="8ab03-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="8ab03-112">Aşağıdaki çizimler, bu özellikleri kullanarak araç ipucu konumlandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="8ab03-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="8ab03-113">Ancak, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bu çizimler örneklerde Göster tarafından tanımlanan özelliklerin nasıl ayarlanacağını <xref:System.Windows.Controls.ToolTip> sınıfı, karşılık gelen özelliklere <xref:System.Windows.Controls.ToolTipService> sınıfı, aynı düzen kurallarını uygulayın.</span><span class="sxs-lookup"><span data-stu-id="8ab03-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="8ab03-114">Yerleştirme özelliği için olası değerler hakkında daha fazla bilgi için bkz: [açılan yerleştirme davranışını](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="8ab03-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).</span></span>  
  
 <span data-ttu-id="8ab03-115">![Araç İpucu yerleştirme](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span><span class="sxs-lookup"><span data-stu-id="8ab03-115">![ToolTip placement](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")</span></span>  
<span data-ttu-id="8ab03-116">Yerleştirme özelliği kullanarak araç ipucu yerleşimi</span><span class="sxs-lookup"><span data-stu-id="8ab03-116">ToolTip placement by using the Placement property</span></span>  
  
 <span data-ttu-id="8ab03-117">![Bir araç ipucu yerleştirme dikdörtgen kullanarak yerleştirme](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span><span class="sxs-lookup"><span data-stu-id="8ab03-117">![Placing a ToolTip by using a placement rectangle](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")</span></span>  
<span data-ttu-id="8ab03-118">Yerleştirme ve YerleştirmeDikdörtgeni özellikleri kullanarak araç ipucu yerleşimi</span><span class="sxs-lookup"><span data-stu-id="8ab03-118">ToolTip placement by using the Placement and PlacementRectangle properties</span></span>  
  
 <span data-ttu-id="8ab03-119">![ToolTip yerleşimi diyagramı](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span><span class="sxs-lookup"><span data-stu-id="8ab03-119">![ToolTip placement diagram](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")</span></span>  
<span data-ttu-id="8ab03-120">Yerleştirme, YerleştirmeDikdörtgeni ve sapma özellikleri kullanarak araç ipucu yerleşimi</span><span class="sxs-lookup"><span data-stu-id="8ab03-120">ToolTip placement by using the Placement, PlacementRectangle, and Offset properties</span></span>  
  
 <span data-ttu-id="8ab03-121">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTip> içerikleri olan bir araç ipucu konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8ab03-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="8ab03-122">Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService> içerikleri değil bir araç ipucu konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesnesi.</span><span class="sxs-lookup"><span data-stu-id="8ab03-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="8ab03-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8ab03-123">See Also</span></span>  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [<span data-ttu-id="8ab03-124">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="8ab03-124">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [<span data-ttu-id="8ab03-125">Araç İpucuna Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="8ab03-125">ToolTip Overview</span></span>](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [<span data-ttu-id="8ab03-126">Araç İpucu servisi ve ContextMenuService kullanın</span><span class="sxs-lookup"><span data-stu-id="8ab03-126">Use the ContextMenuService and ToolTipService</span></span>](http://msdn.microsoft.com/library/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
