---
title: 'Nasıl yapılır: Araç İpucu Konumlandırma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
ms.openlocfilehash: 811818fe6e7c0d8ce9e2aa058b42bf592ada4b92
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59212355"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="9e39f-102">Nasıl yapılır: Araç İpucu Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="9e39f-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="9e39f-103">Bu örnek, ekranda bir araç ipucunun konumunu belirtmek gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e39f-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e39f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e39f-104">Example</span></span>  
 <span data-ttu-id="9e39f-105">Her ikisinde de tanımlanan beş özellikler kümesini kullanarak bir araç ipucu konumlandırabilirsiniz <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıfları.</span><span class="sxs-lookup"><span data-stu-id="9e39f-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="9e39f-106">Aşağıdaki tabloda, bu iki özellik kümeleri beş gösterir ve sınıf göre kendi başvuru belgelerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="9e39f-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="9e39f-107">Karşılık gelen araç ipucu özelliklere göre sınıfı</span><span class="sxs-lookup"><span data-stu-id="9e39f-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="9e39f-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Sınıf özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e39f-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="9e39f-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Sınıf özellikleri</span><span class="sxs-lookup"><span data-stu-id="9e39f-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="9e39f-110">Kullanarak bir araç ipucu içeriğini tanımlarsanız, bir <xref:System.Windows.Controls.ToolTip> nesnesi ya da sınıf özelliklerini kullanabilirsiniz; ancak <xref:System.Windows.Controls.ToolTipService> özellikleri daha önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="9e39f-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="9e39f-111">Kullanım <xref:System.Windows.Controls.ToolTipService> olarak tanımlanmamış araç ipuçları için özellikleri <xref:System.Windows.Controls.ToolTip> nesneleri.</span><span class="sxs-lookup"><span data-stu-id="9e39f-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="9e39f-112">Aşağıdaki çizimler, bu özellikleri kullanarak tooltip konumlandırma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="9e39f-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="9e39f-113">Ancak, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler, bu örnekler tarafından tanımlanan özelliklerin nasıl ayarlanacağını <xref:System.Windows.Controls.ToolTip> sınıfı, karşılık gelen özelliklere <xref:System.Windows.Controls.ToolTipService> sınıfı aynı düzen kurallarını izleyin.</span><span class="sxs-lookup"><span data-stu-id="9e39f-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="9e39f-114">Yerleştirme özelliği için olası değerler hakkında daha fazla bilgi için bkz: [açılan pencere yerleştirme davranışı](popup-placement-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="9e39f-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  
 
 <span data-ttu-id="9e39f-115">Aşağıdaki görüntüde, yerleştirme özelliğini kullanarak araç ipucu yerleşimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9e39f-115">The following image shows tooltip placement by using the Placement property:</span></span>  
  
 ![Araç İpucu yerleştirme yerleştirme özelliğini kullanarak gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 <span data-ttu-id="9e39f-117">Aşağıdaki görüntüde yerleştirme ve PlacementRectangle özelliklerinin kullanarak araç ipucu yerleşimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9e39f-117">The following image shows tooltip placement by using the Placement and PlacementRectangle properties:</span></span>   

 ![Araç İpucu yerleştirme PlacementRectangle özelliğini kullanarak gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 <span data-ttu-id="9e39f-119">Aşağıdaki görüntüde, yerleştirme ve PlacementRectangle uzaklığı özelliklerini kullanarak araç ipucu yerleşimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="9e39f-119">The following image shows tooltip placement by using the Placement, PlacementRectangle, and Offset properties:</span></span>   
  
 ![Araç İpucu yerleştirme uzaklığı özelliğini kullanarak gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <span data-ttu-id="9e39f-121">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTip> içeriğe sahip olan bir araç ipucunun konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesne.</span><span class="sxs-lookup"><span data-stu-id="9e39f-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="9e39f-122">Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService> içeriğe sahip olmayan bir araç ipucunun konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesne.</span><span class="sxs-lookup"><span data-stu-id="9e39f-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="9e39f-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9e39f-123">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="9e39f-124">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="9e39f-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="9e39f-125">Araç İpucuna Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="9e39f-125">ToolTip Overview</span></span>](tooltip-overview.md)
