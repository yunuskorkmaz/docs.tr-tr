---
title: 'Nasıl yapılır: Olay İşleyicisinde Kaynak Öğesi Bulma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
ms.openlocfilehash: c3ae893cd7fd7780854d6eb6ffd682feadb5c5a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544010"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Nasıl yapılır: Olay İşleyicisinde Kaynak Öğesi Bulma
Bu örnek, bir olay işleyicisi kaynak öğesi bulma gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bir arka plan kodu dosyasında bildirilen olay işleyicisi. Bir kullanıcı işleyici iliştirildiği düğmesine tıkladığında, işleyici özellik değerini değiştirir. İşleyici kod kullanan <xref:System.Windows.RoutedEventArgs.Source%2A> özelliği değiştirmek için olay bağımsız değişkeninde bildirilen yönlendirilmiş olay verilerini <xref:System.Windows.FrameworkElement.Width%2A> özellik değerine <xref:System.Windows.RoutedEventArgs.Source%2A> öğesi.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Windows.RoutedEventArgs>  
 [Yönlendirilmiş Olaylara Genel Bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
