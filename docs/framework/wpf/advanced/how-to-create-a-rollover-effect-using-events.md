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
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005185"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a>Nasıl yapılır: Olayları Kullanarak Geçiş Efekti Oluşturma
Bu örnek, fare işaretçisi öğe tarafından dolu olan alana girdiğinde bir öğenin renginin nasıl değiştirileceğini gösterir.  
  
 Bu örnek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasından ve arka plan kod dosyasından oluşur.  
  
> [!NOTE]
> Bu örnek, olayların nasıl kullanılacağını gösterir, ancak aynı etkiyi elde etmek için önerilen yol, bir stilde <xref:System.Windows.Trigger> kullanmaktır. Daha fazla bilgi için bkz. [Stil oluşturma ve şablon](../controls/styling-and-templating.md)oluşturma.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, bir <xref:System.Windows.Controls.TextBlock> etrafında <xref:System.Windows.Controls.Border> ' dan oluşan Kullanıcı arabirimini oluşturur ve <xref:System.Windows.Input.Mouse.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicilerini <xref:System.Windows.Controls.Border> ' e ekler.  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 Aşağıdaki kod arkasında <xref:System.Windows.UIElement.MouseEnter> ve <xref:System.Windows.UIElement.MouseLeave> olay işleyicileri oluşturulur.  Fare işaretçisi <xref:System.Windows.Controls.Border> ' ı girdiğinde, <xref:System.Windows.Controls.Border> ' in arka planı kırmızı olarak değiştirilir.  Fare işaretçisi <xref:System.Windows.Controls.Border> ' ı terk ettiğinde, <xref:System.Windows.Controls.Border> ' in arka planı beyaza dönüştürülür.  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
