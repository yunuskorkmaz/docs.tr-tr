---
title: 'Nasıl yapılır: Viewbox İçeriğine Uzatma Özellikleri Uygulama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 08358ea07e0c41e3b7cdf52251a3ed4296035e2d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209885"
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a>Nasıl yapılır: Viewbox İçeriğine Uzatma Özellikleri Uygulama
## <a name="example"></a>Örnek  
 Bu örnekte, değerini değiştirmek gösterilmektedir <xref:System.Windows.Controls.Viewbox.StretchDirection%2A> ve <xref:System.Windows.Controls.Viewbox.Stretch%2A> özelliklerini bir <xref:System.Windows.Controls.Viewbox>.  
  
 İlk örnekte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tanımlamak için bir <xref:System.Windows.Controls.Viewbox> öğesi. Buna atar bir <xref:System.Windows.FrameworkElement.MaxWidth%2A> ve <xref:System.Windows.FrameworkElement.MaxHeight%2A> 400. Örnek gruplandırdığınızda bir <xref:System.Windows.Controls.Image> öğesiyle <xref:System.Windows.Controls.Viewbox>. <xref:System.Windows.Controls.Button> özellik değerleri karşılık gelen öğeleri <xref:System.Windows.Controls.Viewbox.Stretch%2A> ve <xref:System.Windows.Controls.StretchDirection> sıralamaları iç içe uzatma davranışını <xref:System.Windows.Controls.Image>.  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki kod arka plan dosya tanıtıcıları <xref:System.Windows.Controls.Button> <xref:System.Windows.Controls.Primitives.ButtonBase.Click> olayları, önceki [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] örnek tanımlar.  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.Viewbox>
- <xref:System.Windows.Media.Stretch>
- <xref:System.Windows.Controls.StretchDirection>
