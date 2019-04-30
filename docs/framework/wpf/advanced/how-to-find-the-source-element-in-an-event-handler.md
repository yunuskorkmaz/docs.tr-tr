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
ms.openlocfilehash: 9a49878c9ad8313903df4506796998fd43e2e749
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757514"
---
# <a name="how-to-find-the-source-element-in-an-event-handler"></a><span data-ttu-id="f0051-102">Nasıl yapılır: Olay İşleyicisinde Kaynak Öğesi Bulma</span><span class="sxs-lookup"><span data-stu-id="f0051-102">How to: Find the Source Element in an Event Handler</span></span>
<span data-ttu-id="f0051-103">Bu örnekte, olay işleyicisinde kaynak öğesi bulma gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="f0051-103">This example shows how to find the source element in an event handler.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0051-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="f0051-104">Example</span></span>  
 <span data-ttu-id="f0051-105">Aşağıdaki örnekte gösterildiği bir <xref:System.Windows.Controls.Primitives.ButtonBase.Click> bir arka plan kod dosyasında bildirilen olay işleyicisi.</span><span class="sxs-lookup"><span data-stu-id="f0051-105">The following example shows a <xref:System.Windows.Controls.Primitives.ButtonBase.Click> event handler that is declared in a code-behind file.</span></span> <span data-ttu-id="f0051-106">Bir kullanıcı işleyici iliştirildiği düğmesine tıkladığında, işleyici özellik değerini değiştirir.</span><span class="sxs-lookup"><span data-stu-id="f0051-106">When a user clicks the button that the handler is attached to, the handler changes a property value.</span></span> <span data-ttu-id="f0051-107">İşleyici kod <xref:System.Windows.RoutedEventArgs.Source%2A> olay bağımsız değişkenlerini değiştirmek için bildirilen yönlendirilmiş olayı verileri özelliği <xref:System.Windows.FrameworkElement.Width%2A> özellik değerine <xref:System.Windows.RoutedEventArgs.Source%2A> öğesi.</span><span class="sxs-lookup"><span data-stu-id="f0051-107">The handler code uses the <xref:System.Windows.RoutedEventArgs.Source%2A> property of the routed event data that is reported in the event arguments to change the <xref:System.Windows.FrameworkElement.Width%2A> property value on the <xref:System.Windows.RoutedEventArgs.Source%2A> element.</span></span>  
  
 [!code-xaml[RoutedEventSource#XAMLHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml#xamlhandler)]  
  
 [!code-csharp[RoutedEventSource#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/RoutedEventSource/CSharp/default.xaml.cs#handler)]
 [!code-vb[RoutedEventSource#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RoutedEventSource/VisualBasic/default.xaml.vb#handler)]  
  
## <a name="see-also"></a><span data-ttu-id="f0051-108">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0051-108">See also</span></span>

- <xref:System.Windows.RoutedEventArgs>
- [<span data-ttu-id="f0051-109">Yönlendirilmiş Olaylara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="f0051-109">Routed Events Overview</span></span>](routed-events-overview.md)
- [<span data-ttu-id="f0051-110">Nasıl Yapılır Konuları</span><span class="sxs-lookup"><span data-stu-id="f0051-110">How-to Topics</span></span>](events-how-to-topics.md)
