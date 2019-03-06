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
ms.openlocfilehash: 8c1ff53e5af1ddfda17328291c5e22b57a8fe0e2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57359477"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a>Nasıl yapılır: Olay İşleyicisinde Kaynak Öğesi Bulma
Bu örnekte, olay işleyicisinde kaynak öğesi bulma gösterilmektedir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bir arka plan kod dosyasında bildirilen olay işleyicisi. Bir kullanıcı işleyici iliştirildiği düğmesine tıkladığında, işleyici özellik değerini değiştirir. İşleyici kod <xref:System.Windows.RoutedEventArgs.Source%2A> olay bağımsız değişkenlerini değiştirmek için bildirilen yönlendirilmiş olayı verileri özelliği <xref:System.Windows.FrameworkElement.Width%2A> özellik değerine <xref:System.Windows.RoutedEventArgs.Source%2A> öğesi.  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Windows.RoutedEventArgs>
- [Yönlendirilmiş Olaylara Genel Bakış](routed-events-overview.md)
- [Nasıl Yapılır Konuları](events-how-to-topics.md)
