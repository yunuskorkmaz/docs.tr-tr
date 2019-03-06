---
title: 'Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
ms.openlocfilehash: 6605a6a56fba587678227f5826982ec3266b153c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356305"
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama
Bu örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.StackPanel.Orientation%2A> içinde içeriğinin bir <xref:System.Windows.Controls.StackPanel> öğesi ve nasıl ayarlanacağını <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> alt içeriği.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç oluşturur <xref:System.Windows.Controls.ListBox> öğelerinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Her <xref:System.Windows.Controls.ListBox> olası değerlerini temsil eden <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliklerini bir <xref:System.Windows.Controls.StackPanel>. Bir kullanıcı seçtiğinde bir değer birinde <xref:System.Windows.Controls.ListBox> öğeleri, ilişkili özelliğini <xref:System.Windows.Controls.StackPanel> ve alt <xref:System.Windows.Controls.Button> öğelerini değiştirme.  
  
 [!code-xaml[StackPanelIntroSamp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki arka plan kod dosyası ile ilişkili olaylara değişiklikleri tanımladığına <xref:System.Windows.Controls.ListBox> seçim değişir. <xref:System.Windows.Controls.StackPanel> tarafından tanımlanan <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>
- <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>
- [Panellere Genel Bakış](panels-overview.md)
