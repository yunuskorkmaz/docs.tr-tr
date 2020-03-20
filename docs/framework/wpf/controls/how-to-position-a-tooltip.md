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
# <a name="how-to-position-a-tooltip"></a>Nasıl yapılır: ToolTip Konumlandırma
Bu örnek, bir araç ucunun ekranda konumunu nasıl belirtini gösteriş yaptığıdır.  
  
## <a name="example"></a>Örnek  
 Hem sınıflarda hem de <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTipService> sınıflarda tanımlanan beş özellikkümesini kullanarak bir araç ucunu konumlandırabilirsiniz. Aşağıdaki tablo, beş özellikten oluşan bu iki kümeyi gösterir ve sınıfa göre başvuru belgelerine bağlantılar sağlar.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Sınıfa göre karşılık gelen araç ucu özellikleri  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>sınıf özellikleri|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>sınıf özellikleri|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Bir araç ucunun içeriğini bir <xref:System.Windows.Controls.ToolTip> nesne kullanarak tanımlarsanız, her iki sınıfın özelliklerini kullanabilirsiniz; ancak, <xref:System.Windows.Controls.ToolTipService> özellikleri önceliklidir. Nesne <xref:System.Windows.Controls.ToolTipService> olarak <xref:System.Windows.Controls.ToolTip> tanımlanmayan araç ipuçları için özellikleri kullanın.  
  
 Aşağıdaki çizimler, bu özellikleri kullanarak bir araç ucunun nasıl konumlandırılabildiğini gösterir. Bu çizimlerdeki [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler <xref:System.Windows.Controls.ToolTip> sınıf tarafından tanımlanan özelliklerin nasıl ayarlanış yapılacağını gösterse <xref:System.Windows.Controls.ToolTipService> de, sınıfın karşılık gelen özellikleri aynı düzen kurallarını izler. Yerleşim özelliği için olası değerler hakkında daha fazla bilgi için [Popup Yerleştirme Davranışı'na](popup-placement-behavior.md)bakın.  

 Aşağıdaki resimde, Yerleştirme özelliğikullanılarak araç ipucu yerleşimi gösterilmektedir:  
  
 ![Yerleştirme özelliğini kullanarak Araç İpucu yerleşimini gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)

 Aşağıdaki resimde, Yerleştirme ve YerleştirmeDikdörtgen özelliklerini kullanarak araç ipucu yerleşimi gösterilmektedir:

 ![PlacementRectangle özelliğini kullanarak Araç İpucu yerleşimini gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  

 Aşağıdaki resimde, Yerleştirme, YerleştirmeRectangle ve Ofset özelliklerini kullanarak araç ipucu yerleşimi gösterilmektedir:
  
 ![Ofset özelliğini kullanarak Araç İpucu yerleşimini gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 Aşağıdaki örnekte, içeriği <xref:System.Windows.Controls.ToolTip> <xref:System.Windows.Controls.ToolTip> nesne olan bir araç ucunun konumunu belirtmek için özelliklerin nasıl kullanılacağı gösterilmektedir.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Aşağıdaki örnekte, içeriği <xref:System.Windows.Controls.ToolTipService> <xref:System.Windows.Controls.ToolTip> nesne olmayan bir araç ucunun konumunu belirtmek için özelliklerin nasıl kullanılacağı gösterilmektedir.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Nasıl Dır Konular](tooltip-how-to-topics.md)
- [ToolTip Genel Bakışı](tooltip-overview.md)
