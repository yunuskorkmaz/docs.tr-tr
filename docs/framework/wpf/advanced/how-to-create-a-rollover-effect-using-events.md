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
ms.openlocfilehash: 87740a215136863199d962a2704cf691f27fc3bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776655"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma
Bu örnek, fare işaretçisini girer ve öğe tarafından kapladığı alanı bırakır gibi bir öğenin rengini değiştirme gösterir.  
  
 Bu örnekte oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.  
  
> [!NOTE]
>  Bu örnek olayların nasıl gösterir, ancak bu aynı etkiyi elde etmek için önerilen yöntem kullanmaktır bir <xref:System.Windows.Trigger> stil. Daha fazla bilgi için [stil ve şablon oluşturma](../controls/styling-and-templating.md).  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] oluşur kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Border> etrafında bir <xref:System.Windows.Controls.TextBlock>ve ekler <xref:System.Windows.Input.Mouse.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicilerine <xref:System.Windows.Controls.Border>.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Aşağıdaki kod oluşturur <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicileri.  Fare işaretçisi girdiğinde <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> kırmızıya değiştirilir.  Fare işaretçisi ayrıldığında <xref:System.Windows.Controls.Border>, arka planını <xref:System.Windows.Controls.Border> beyaz olarak değiştirilir.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
