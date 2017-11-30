---
title: "Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama"
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
- StackPanel control [WPF], content alignment [WPF]
- content alignment [WPF]
- aligning [WPF], content
ms.assetid: c1e8f962-72c8-4e7a-8670-7a2d7e021791
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bccf0455c736d14bd77113841603022d4c362787
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-horizontally-or-vertically-align-content-in-a-stackpanel"></a>Nasıl yapılır: StackPanel İçinde Yatay veya Dikey Olarak İçerik Hizalama
Bu örnek nasıl ayarlanacağını gösterir <xref:System.Windows.Controls.StackPanel.Orientation%2A> içindeki içeriğin bir <xref:System.Windows.Controls.StackPanel> öğesi ve nasıl ayarlanacağını <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> alt içerik.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, üç oluşturur <xref:System.Windows.Controls.ListBox> öğelerinde [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Her <xref:System.Windows.Controls.ListBox> olası değerlerini temsil eden <xref:System.Windows.Controls.StackPanel.Orientation%2A>, <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>, ve <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> özelliklerini bir <xref:System.Windows.Controls.StackPanel>. Bir kullanıcı seçtiğinde bir değer hiçbirinde <xref:System.Windows.Controls.ListBox> öğeleri, ilişkili özelliğinin <xref:System.Windows.Controls.StackPanel> ve alt <xref:System.Windows.Controls.Button> öğelerini değiştirme.  
  
 [!code-xaml[StackPanelIntroSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml#1)]  
  
 Aşağıdaki arka plan kod dosyası ile ilişkili olaylar değişiklikleri tanımlar <xref:System.Windows.Controls.ListBox> seçim değişir. <xref:System.Windows.Controls.StackPanel>tarafından tanımlanan <xref:System.Windows.FrameworkElement.Name%2A> `sp1`.  
  
 [!code-csharp[StackPanelIntroSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelIntroSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[StackPanelIntroSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelIntroSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>  
 <xref:System.Windows.FrameworkElement.VerticalAlignment%2A>  
 [Paneller Genel Bakış](../../../../docs/framework/wpf/controls/panels-overview.md)
