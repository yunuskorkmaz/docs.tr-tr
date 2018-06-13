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
ms.openlocfilehash: d458d87586614093b35fcd73969dea04fe620351
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543016"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma
Bu örnek, fare işaretçisini girer ve öğe tarafından kapladığı alanı terk gibi bir öğesinin rengini değiştirmek gösterilmiştir.  
  
 Bu örnek oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.  
  
> [!NOTE]
>  Örnek olaylar kullanmayı gösterir, ancak bu aynı sonucu elde etmek için önerilen yöntem kullanmaktır bir <xref:System.Windows.Trigger> stilinde. Daha fazla bilgi için bkz: [stil ve şablon](../../../../docs/framework/wpf/controls/styling-and-templating.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşan kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Border> geçici bir <xref:System.Windows.Controls.TextBlock>ve ekler <xref:System.Windows.Input.Mouse.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicilerine <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Aşağıdaki arka plan kodu oluşturur <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicileri.  Fare işaretçisini girdiğinde <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> kırmızı değiştirilir.  Fare işaretçisini ayrıldığında <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> beyaza geri değişir.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
