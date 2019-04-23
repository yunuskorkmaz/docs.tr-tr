---
title: 'Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus events [WPF], changing element color for
- colors of elements [WPF], changing
- elements [WPF], changing color of
ms.assetid: 7e246802-3625-47a7-ae9d-c8a2a40fd040
ms.openlocfilehash: 744963cc543110121a777e1d4c3cdcb3cec40d9e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217646"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme
Bu örnek, kazançlar ve odağından kullanarak öğenin rengini değiştirme gösterir <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olayları.  
  
 Bu örnekte oluşan bir [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyası ve bir arka plan kod dosyası.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] iki oluşur kullanıcı arabirimi oluşturan <xref:System.Windows.Controls.Button> nesneleri ve ekler için olay işleyicileri <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olayları <xref:System.Windows.Controls.Button> nesneleri.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Aşağıdaki kod oluşturur <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olay işleyicileri.  Zaman <xref:System.Windows.Controls.Button> klavye odağı kazandığında <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> kırmızıya değiştirilir.  Zaman <xref:System.Windows.Controls.Button> klavye odağından <xref:System.Windows.Controls.Control.Background%2A> , <xref:System.Windows.Controls.Button> beyaz olarak değiştirilir.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
