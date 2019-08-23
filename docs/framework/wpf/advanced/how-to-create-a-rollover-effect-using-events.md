---
title: 'Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 3996a3b9bb976dd5f2e5b675de3894bbaba7d9d3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69960381"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma
Bu örnek, fare işaretçisi öğe tarafından dolu olan alana girdiğinde bir öğenin renginin nasıl değiştirileceğini gösterir.  
  
 Bu örnek, bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosya ve arka plan kod dosyasından oluşur.  
  
> [!NOTE]
> Bu örnek, olayların nasıl kullanılacağını gösterir, ancak aynı etkiyi elde etmek için önerilen yol, bir <xref:System.Windows.Trigger> stilde kullanmaktır. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] <xref:System.Windows.UIElement.MouseLeave> , <xref:System.Windows.Controls.Border> bir<xref:System.Windows.Controls.TextBlock>öğesininetrafında oluşan Kullanıcı arabirimini oluşturur ve<xref:System.Windows.Controls.Border>ve olay işleyicilerini öğesine ekler. <xref:System.Windows.Input.Mouse.MouseEnter>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Aşağıdaki kod arkasında <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicileri oluşturulur.  Fare işaretçisi öğesine girdiğinde <xref:System.Windows.Controls.Border>, <xref:System.Windows.Controls.Border> öğesinin arka planı kırmızı olarak değişir.  Fare işaretçisi <xref:System.Windows.Controls.Border>' den çıktığında, <xref:System.Windows.Controls.Border> öğesinin arka planı tekrar beyaza değişir.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
