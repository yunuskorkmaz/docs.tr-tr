---
title: 'Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama'
description: Windows Presentation Foundation StackPanel içindeki içerik yönlendirmesini ve alt içeriğin HorizontalAlignment ve VerticalAlignment ayarlarını nasıl ayarlayacağınızı öğrenin.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: d3c7215d8193d1d8a72597c44cf265f5bd400ea1
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/24/2020
ms.locfileid: "87167632"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama
Bu örnekte, <xref:System.Windows.Controls.StackPanel.Orientation%2A> bir öğe içindeki içeriğin nasıl ayarlanacağı <xref:System.Windows.Controls.StackPanel> ve ayrıca alt içeriğin nasıl ayarlanacağı gösterilmektedir <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> .  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek <xref:System.Windows.Controls.ListBox> içinde üç öğe oluşturur [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Her biri <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.StackPanel.Orientation%2A> ,, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve özelliklerinin olası değerlerini temsil eder <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> <xref:System.Windows.Controls.StackPanel> . Bir Kullanıcı herhangi bir öğe içinde bir değer seçtiğinde, <xref:System.Windows.Controls.ListBox> <xref:System.Windows.Controls.StackPanel> ve alt öğelerinin ilişkili özelliği <xref:System.Windows.Controls.Button> değişir.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki arka plan kod dosyası, seçim değişiklikleriyle ilişkili olaylarda yapılan değişiklikleri tanımlar <xref:System.Windows.Controls.ListBox> . <xref:System.Windows.Controls.StackPanel>tarafından tanımlanır <xref:System.Windows.FrameworkElement.Name%2A> `sp1` .  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Panellere Genel Bakış](panels-overview.md)
