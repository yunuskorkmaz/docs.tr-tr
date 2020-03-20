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
ms.openlocfilehash: 0f52703e4fe127daa40f220280f084b2026580cc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186947"
---
# <a name="how-to-position-a-tooltip"></a><span data-ttu-id="10101-102">Nasıl yapılır: ToolTip Konumlandırma</span><span class="sxs-lookup"><span data-stu-id="10101-102">How to: Position a ToolTip</span></span>
<span data-ttu-id="10101-103">Bu örnek, bir araç ucunun ekranda konumunu nasıl belirtini gösteriş yaptığıdır.</span><span class="sxs-lookup"><span data-stu-id="10101-103">This example shows how to specify the position of a tooltip on the screen.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10101-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="10101-104">Example</span></span>  
 <span data-ttu-id="10101-105">Hem sınıflarda hem de <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> sınıflarda tanımlanan beş özellikkümesini kullanarak bir araç ucunu konumlandırabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="10101-105">You can position a tooltip by using a set of five properties that are defined in both the <xref:System.Windows.Controls.ToolTip> and <xref:System.Windows.Controls.ToolTipService> classes.</span></span> <span data-ttu-id="10101-106">Aşağıdaki tablo, beş özellikten oluşan bu iki kümeyi gösterir ve sınıfa göre başvuru belgelerine bağlantılar sağlar.</span><span class="sxs-lookup"><span data-stu-id="10101-106">The following table shows these two sets of five properties and provides links to their reference documentation according to class.</span></span>  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a><span data-ttu-id="10101-107">Sınıfa göre karşılık gelen araç ucu özellikleri</span><span class="sxs-lookup"><span data-stu-id="10101-107">Corresponding tooltip properties according to class</span></span>  
  
|<span data-ttu-id="10101-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>sınıf özellikleri</span><span class="sxs-lookup"><span data-stu-id="10101-108"><xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> class properties</span></span>|<span data-ttu-id="10101-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>sınıf özellikleri</span><span class="sxs-lookup"><span data-stu-id="10101-109"><xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> class properties</span></span>|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="10101-110">Bir araç ucunun içeriğini bir <xref:System.Windows.Controls.ToolTip> nesne kullanarak tanımlarsanız, her iki sınıfın özelliklerini kullanabilirsiniz; ancak, <xref:System.Windows.Controls.ToolTipService> özellikleri önceliklidir.</span><span class="sxs-lookup"><span data-stu-id="10101-110">If you define the contents of a tooltip by using a <xref:System.Windows.Controls.ToolTip> object, you can use the properties of either class; however, the <xref:System.Windows.Controls.ToolTipService> properties take precedence.</span></span> <span data-ttu-id="10101-111">Nesne <xref:System.Windows.Controls.ToolTipService> olarak <xref:System.Windows.Controls.ToolTip> tanımlanmayan araç ipuçları için özellikleri kullanın.</span><span class="sxs-lookup"><span data-stu-id="10101-111">Use the <xref:System.Windows.Controls.ToolTipService> properties for tooltips that are not defined as <xref:System.Windows.Controls.ToolTip> objects.</span></span>  
  
 <span data-ttu-id="10101-112">Aşağıdaki çizimler, bu özellikleri kullanarak bir araç ucunun nasıl konumlandırılabildiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="10101-112">The following illustrations show how to position a tooltip by using these properties.</span></span> <span data-ttu-id="10101-113">Bu çizimlerdeki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler <xref:System.Windows.Controls.ToolTip> sınıf tarafından tanımlanan özelliklerin nasıl ayarlanış yapılacağını gösterse <xref:System.Windows.Controls.ToolTipService> de, sınıfın karşılık gelen özellikleri aynı düzen kurallarını izler.</span><span class="sxs-lookup"><span data-stu-id="10101-113">Although, the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples in these illustrations show how to set the properties that are defined by the <xref:System.Windows.Controls.ToolTip> class, the corresponding properties of the <xref:System.Windows.Controls.ToolTipService> class follow the same layout rules.</span></span> <span data-ttu-id="10101-114">Yerleşim özelliği için olası değerler hakkında daha fazla bilgi için [Popup Yerleştirme Davranışı'na](popup-placement-behavior.md)bakın.</span><span class="sxs-lookup"><span data-stu-id="10101-114">For more information about the possible values for the Placement property, see [Popup Placement Behavior](popup-placement-behavior.md).</span></span>  

 <span data-ttu-id="10101-115">Aşağıdaki resimde, Yerleştirme özelliğikullanılarak araç ipucu yerleşimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="10101-115">The following image shows tooltip placement by using the Placement property:</span></span>  
  
 ![Yerleştirme özelliğini kullanarak Araç İpucu yerleşimini gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 <span data-ttu-id="10101-117">Aşağıdaki resimde, Yerleştirme ve YerleştirmeDikdörtgen özelliklerini kullanarak araç ipucu yerleşimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="10101-117">The following image shows tooltip placement by using the Placement and PlacementRectangle properties:</span></span>

 ![PlacementRectangle özelliğini kullanarak Araç İpucu yerleşimini gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 <span data-ttu-id="10101-119">Aşağıdaki resimde, Yerleştirme, YerleştirmeRectangle ve Ofset özelliklerini kullanarak araç ipucu yerleşimi gösterilmektedir:</span><span class="sxs-lookup"><span data-stu-id="10101-119">The following image shows tooltip placement by using the Placement, PlacementRectangle, and Offset properties:</span></span>
  
 ![Ofset özelliğini kullanarak Araç İpucu yerleşimini gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 <span data-ttu-id="10101-121">Aşağıdaki örnekte, içeriği <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTip> nesne olan bir araç ucunun konumunu belirtmek için özelliklerin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10101-121">The following example shows how to use the <xref:System.Windows.Controls.ToolTip> properties to specify the position of a tooltip whose content is a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 <span data-ttu-id="10101-122">Aşağıdaki örnekte, içeriği <xref:System.Windows.Controls.ToolTipService> <xref:System.Windows.Controls.ToolTip> nesne olmayan bir araç ucunun konumunu belirtmek için özelliklerin nasıl kullanılacağı gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="10101-122">The following example shows how to use the <xref:System.Windows.Controls.ToolTipService> properties to specify the position of a tooltip whose content is not a <xref:System.Windows.Controls.ToolTip> object.</span></span>  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a><span data-ttu-id="10101-123">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="10101-123">See also</span></span>

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [<span data-ttu-id="10101-124">Nasıl Dır Konular</span><span class="sxs-lookup"><span data-stu-id="10101-124">How-to Topics</span></span>](tooltip-how-to-topics.md)
- [<span data-ttu-id="10101-125">ToolTip Genel Bakışı</span><span class="sxs-lookup"><span data-stu-id="10101-125">ToolTip Overview</span></span>](tooltip-overview.md)
