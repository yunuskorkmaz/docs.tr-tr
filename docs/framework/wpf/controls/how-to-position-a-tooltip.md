---
title: "Nasıl yapılır: ToolTip Konumlandırma"
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
- ToolTip control [WPF], positioning
- positioning ToolTip controls [WPF]
ms.assetid: cddf3757-9e5f-4ce3-a6eb-44489cf3804a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0e8345b74cf9269bca21e1e5698de974109c2aee
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-position-a-tooltip"></a>Nasıl yapılır: ToolTip Konumlandırma
Bu örnek ekranda araç ipucu konumunu belirtmek nasıl gösterir.  
  
## <a name="example"></a>Örnek  
 İkisi de tanımlanan beş özellikler kümesini kullanarak bir araç ipucu yerleştirebilirsiniz <xref:System.Windows.Controls.ToolTip> ve <xref:System.Windows.Controls.ToolTipService> sınıfları. Aşağıdaki tabloda bu iki beş özelliklerinin gösterir ve sınıf göre kendi referans belgelerine ait bağlantılar sağlanmıştır.  
  
### <a name="corresponding-tooltip-properties-according-to-class"></a>Karşılık gelen araç ipucu özelliklere göre sınıfı  
  
|<xref:System.Windows.Controls.ToolTip?displayProperty=nameWithType>Sınıf özellikleri|<xref:System.Windows.Controls.ToolTipService?displayProperty=nameWithType>Sınıf özellikleri|  
|--------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.Windows.Controls.ToolTip.Placement%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.Placement%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementTarget%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementTarget%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.PlacementRectangle%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.PlacementRectangle%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.HorizontalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.HorizontalOffset%2A?displayProperty=nameWithType>|  
|<xref:System.Windows.Controls.ToolTip.VerticalOffset%2A?displayProperty=nameWithType>|<xref:System.Windows.Controls.ToolTipService.VerticalOffset%2A?displayProperty=nameWithType>|  
  
 Bir araç ipucu içeriğini kullanarak tanımlarsanız bir <xref:System.Windows.Controls.ToolTip> nesnesi, her iki sınıfın özelliklerini kullanabilirsiniz; ancak, <xref:System.Windows.Controls.ToolTipService> özellikleri daha önceliklidir. Kullanım <xref:System.Windows.Controls.ToolTipService> olarak tanımlı değil araç ipuçları için özellikleri <xref:System.Windows.Controls.ToolTip> nesneleri.  
  
 Aşağıdaki çizimler, bu özellikleri kullanarak araç ipucu konumlandırma gösterilmektedir. Ancak, [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] bu çizimler örneklerde Göster tarafından tanımlanan özelliklerin nasıl ayarlanacağını <xref:System.Windows.Controls.ToolTip> sınıfı, karşılık gelen özelliklere <xref:System.Windows.Controls.ToolTipService> sınıfı, aynı düzen kurallarını uygulayın. Yerleştirme özelliği için olası değerler hakkında daha fazla bilgi için bkz: [açılan yerleştirme davranışını](../../../../docs/framework/wpf/controls/popup-placement-behavior.md).  
  
 ![Araç İpucu yerleştirme](../../../../docs/framework/wpf/controls/media/tooltipplacement.png "ToolTipPlacement")  
Yerleştirme özelliği kullanarak araç ipucu yerleşimi  
  
 ![Bir araç ipucu yerleştirme dikdörtgen kullanarak yerleştirme](../../../../docs/framework/wpf/controls/media/tooltipplacementrectangle.png "ToolTipPlacementRectangle")  
Yerleştirme ve YerleştirmeDikdörtgeni özellikleri kullanarak araç ipucu yerleşimi  
  
 ![ToolTip yerleşimi diyagramı](../../../../docs/framework/wpf/controls/media/tooltipplacementprhv.png "ToolTipPlacementPRHV")  
Yerleştirme, YerleştirmeDikdörtgeni ve sapma özellikleri kullanarak araç ipucu yerleşimi  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTip> içerikleri olan bir araç ipucu konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesnesi.  
  
 [!code-xaml[ToolTipService#ToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#tooltip)]  
  
 [!code-csharp[ToolTipService#ToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#tooltipcode)]
 [!code-vb[ToolTipService#ToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#tooltipcode)]  
  
 Aşağıdaki örnekte nasıl kullanılacağını gösterir <xref:System.Windows.Controls.ToolTipService> içerikleri değil bir araç ipucu konumunu belirtmek için özellikleri bir <xref:System.Windows.Controls.ToolTip> nesnesi.  
  
 [!code-xaml[ToolTipService#NoToolTip](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml#notooltip)]  
  
 [!code-csharp[ToolTipService#NoToolTipCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolTipService/CSharp/Pane1.xaml.cs#notooltipcode)]
 [!code-vb[ToolTipService#NoToolTipCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ToolTipService/visualbasic/pane1.xaml.vb#notooltipcode)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.ToolTip>  
 <xref:System.Windows.Controls.ToolTipService>  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/controls/tooltip-how-to-topics.md)  
 [Araç İpucu genel bakış](../../../../docs/framework/wpf/controls/tooltip-overview.md)  
 [Araç İpucu servisi ve ContextMenuService kullanın](http://msdn.microsoft.com/en-us/809b0e9c-d612-4cda-b8af-1a698c68f4d1)
