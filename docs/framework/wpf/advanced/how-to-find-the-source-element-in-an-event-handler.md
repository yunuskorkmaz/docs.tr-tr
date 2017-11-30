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
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="c979a-102">Nasıl yapılır: Olay İşleyicisinde Kaynak Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="c979a-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="c979a-103">Bu örnek, bir olay işleyicisi kaynak öğesi bulma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="c979a-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c979a-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="c979a-104">Example</span></span>  
 <span data-ttu-id="c979a-105">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bir arka plan kodu dosyasında bildirilen olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="c979a-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="c979a-106">Bir kullanıcı işleyici iliştirildiği düğmesine tıkladığında, işleyici özellik değerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="c979a-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="c979a-107">İşleyici kod kullanan <xref:System.Windows.RoutedEventArgs.Source%2A> özelliği değiştirmek için olay bağımsız değişkeninde bildirilen yönlendirilmiş olay verilerini <xref:System.Windows.FrameworkElement.Width%2A> özellik değerine <xref:System.Windows.RoutedEventArgs.Source%2A> öğesi.</span><span class="sxs-lookup"><span data-stu-id="c979a-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="c979a-108">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c979a-108">See Also</span></span>  
 <xref:System.Windows.RoutedEventArgs>  
 [<span data-ttu-id="c979a-109">Yönlendirilmiş olaylara genel bakış</span><span class="sxs-lookup"><span data-stu-id="c979a-109">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)  
 [<span data-ttu-id="c979a-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="c979a-110">How-to Topics</span></span>](../../../../docs/framework/wpf/advanced/events-how-to-topics.md)
