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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61770935"
---
# <a name="how-to-position-a-tooltip"></a>Nasıl yapılır: Araç İpucu Konumlandırma
Bu örnek, ekranda bir araç ipucunun konumunu belirtmek gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Her ikisinde de tanımlanan beş özellikler kümesini kullanarak bir araç ipucu konumlandırabilirsiniz <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıfları. Aşağıdaki tabloda, bu iki özellik kümeleri beş gösterir ve sınıf göre kendi başvuru belgelerine bağlantılar sağlar.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Karşılık gelen araç ipucu özelliklere göre sınıfı  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType> Sınıf özellikleri|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType> Sınıf özellikleri|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Kullanarak bir araç ipucu içeriğini tanımlarsanız, bir <xref:System.Windows.Controls.ToolTip> nesnesi ya da sınıf özelliklerini kullanabilirsiniz; ancak <xref:System.Windows.Controls.ToolTipService> özellikleri daha önceliklidir. Kullanım <xref:System.Windows.Controls.ToolTipService> olarak tanımlanmamış araç ipuçları için özellikleri <xref:System.Windows.Controls.ToolTip> nesneleri.  
  
 Aşağıdaki çizimler, bu özellikleri kullanarak tooltip konumlandırma gösterilmektedir. Ancak, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] örnekler, bu örnekler tarafından tanımlanan özelliklerin nasıl ayarlanacağını <xref:System.Windows.Controls.ToolTip> sınıfı, karşılık gelen özelliklere <xref:System.Windows.Controls.ToolTipService> sınıfı aynı düzen kurallarını izleyin. Yerleştirme özelliği için olası değerler hakkında daha fazla bilgi için bkz: [açılan pencere yerleştirme davranışı](popup-placement-behavior.md).  
 
 Aşağıdaki görüntüde, yerleştirme özelliğini kullanarak araç ipucu yerleşimi gösterilmektedir:  
  
 ![Araç İpucu yerleştirme yerleştirme özelliğini kullanarak gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-property.png)
 
 Aşağıdaki görüntüde yerleştirme ve PlacementRectangle özelliklerinin kullanarak araç ipucu yerleşimi gösterilmektedir:   

 ![Araç İpucu yerleştirme PlacementRectangle özelliğini kullanarak gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-rectangle-property.png)  
 
 Aşağıdaki görüntüde, yerleştirme ve PlacementRectangle uzaklığı özelliklerini kullanarak araç ipucu yerleşimi gösterilmektedir:   
  
 ![Araç İpucu yerleştirme uzaklığı özelliğini kullanarak gösteren diyagram.](./media/how-to-position-a-tooltip/tooltip-placement-offset-property.png)

 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTip> içeriğe sahip olan bir araç ipucunun konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesne.  
  
 [!code-xaml[ToolTipService#ToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Aşağıdaki örnek nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService> içeriğe sahip olmayan bir araç ipucunun konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesne.  
  
 [!code-xaml[ToolTipService#NoToolTip](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.ToolTip>
- <xref:System.Windows.Controls.ToolTipService>
- [Nasıl Yapılır Konuları](tooltip-how-to-topics.md)
- [Araç İpucuna Genel Bakış](tooltip-overview.md)
