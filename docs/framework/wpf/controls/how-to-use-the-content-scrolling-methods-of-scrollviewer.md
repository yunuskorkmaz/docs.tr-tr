---
title: "Nasıl yapılır: ScrollViewer'ın İçerik Kaydırma Yöntemlerini Kullanma"
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
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: dc9b79ae9b8078bbdc4c41fb0c952237f86fcac8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="2b67a-102">Nasıl yapılır: ScrollViewer'ın İçerik Kaydırma Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="2b67a-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="2b67a-103">Bu örnek kaydırma yöntemlerinin kullanmayı gösterir <xref:System.Windows.Controls.ScrollViewer> öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b67a-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="2b67a-104">Artımlı içeriğin satırı veya sayfa, kaydırma bu yöntemleri sağlayan bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2b67a-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2b67a-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="2b67a-105">Example</span></span>  
 <span data-ttu-id="2b67a-106">Aşağıdaki örnekte bir <xref:System.Windows.Controls.ScrollViewer> adlı `sv1`, bir alt barındıran <xref:System.Windows.Controls.TextBlock> öğesi.</span><span class="sxs-lookup"><span data-stu-id="2b67a-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="2b67a-107">Çünkü <xref:System.Windows.Controls.TextBlock> üst büyük <xref:System.Windows.Controls.ScrollViewer>, kaydırma etkinleştirmek için kaydırma çubukları görüntülenir.</span><span class="sxs-lookup"><span data-stu-id="2b67a-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <span data-ttu-id="2b67a-108"><xref:System.Windows.Controls.Button>çeşitli kaydırma yöntemleri gösteren öğeleri yerleşik ayrı bir sol <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="2b67a-108"><xref:System.Windows.Controls.Button> elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="2b67a-109">Her <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya içinde kaydırma davranışını denetleyen ilgili bir özel yöntemi çağırır <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="2b67a-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="2b67a-110">Aşağıdaki örnek kullanır <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> ve <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="2b67a-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="2b67a-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2b67a-111">See Also</span></span>  
 <xref:System.Windows.Controls.ScrollViewer>  
 <xref:System.Windows.Controls.StackPanel>
