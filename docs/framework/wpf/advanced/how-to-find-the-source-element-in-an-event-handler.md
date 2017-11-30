---
title: "Nasıl yapılır: Olay İşleyicisinde Kaynak Öğesi Bulma"
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
- source element in event handlers [WPF]
- event handlers [WPF], finding source element in
ms.assetid: 85f71c5a-b714-4c65-9711-7d905c2bbe98
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e9746683ec5b7ad142591c2b419f9af21be8d69c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
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
 [Yönlendirilmiş olaylara genel bakış](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [Nasıl Yapılır Konuları](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
