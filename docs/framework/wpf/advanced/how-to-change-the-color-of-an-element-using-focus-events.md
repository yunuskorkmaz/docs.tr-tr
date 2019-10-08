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
ms.openlocfilehash: 5c59dc5f2f8f26fac69933f9ef641a3a51306619
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004827"
---
# <a name="how-to-change-the-color-of-an-element-using-focus-events"></a>Nasıl yapılır: Odak Olaylarını Kullanarak Öğenin Rengini Değiştirme
Bu örnek, <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olaylarını kullanarak odak kazanırsa ve kaybettiğinde bir öğenin renginin nasıl değiştirileceğini gösterir.  
  
 Bu örnek [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] dosyasından ve arka plan kod dosyasından oluşur.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki XAML, iki <xref:System.Windows.Controls.Button> nesnesinden oluşan Kullanıcı arabirimini oluşturur ve <xref:System.Windows.Controls.Button> nesnelerine <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olayları için olay işleyicileri ekler.  
  
 [!code-xaml[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml#gotlostfocussamplexaml)]  
  
 Aşağıdaki kod arkasında <xref:System.Windows.UIElement.GotFocus> ve <xref:System.Windows.UIElement.LostFocus> olay işleyicileri oluşturulur.  @No__t-0, klavye odağı aldığında, @no__t 2 ' nin <xref:System.Windows.Controls.Control.Background%2A> ' i kırmızıya değiştirilir.  @No__t-0 klavye odağını kaybettiğinde, <xref:System.Windows.Controls.Button> ' nin <xref:System.Windows.Controls.Control.Background%2A> ' i yeniden beyaza dönüştürülür.  
  
 [!code-csharp[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/CSharp/Window1.xaml.cs#gotlostfocussampleeventhandlers)]
 [!code-vb[gotfocusLostfocusEffectUsingEvent#GotLostFocusSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gotfocusLostfocusEffectUsingEvent/VisualBasic/Window1.xaml.vb#gotlostfocussampleeventhandlers)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Girişe Genel Bakış](input-overview.md)
