---
title: "Nasıl yapılır: ScrollViewer'ın İçerik Kaydırma Yöntemlerini Kullanma"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IScrollInfo interface [WPF]
- scrolling methods [WPF]
- ScrollViewer control [WPF], scrolling methods
ms.assetid: 4708cc65-6510-45f8-82e6-30b0d3e30045
ms.openlocfilehash: e81c63de16d09de8435d5ec49a013bf8dc5927cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59142161"
---
# <a name="how-to-use-the-content-scrolling-methods-of-scrollviewer"></a><span data-ttu-id="6ead2-102">Nasıl yapılır: ScrollViewer'ın İçerik Kaydırma Yöntemlerini Kullanma</span><span class="sxs-lookup"><span data-stu-id="6ead2-102">How to: Use the Content-Scrolling Methods of ScrollViewer</span></span>
<span data-ttu-id="6ead2-103">Bu örnek, kaydırma yöntemlerini kullanma işlemini gösterir. <xref:System.Windows.Controls.ScrollViewer> öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ead2-103">This example shows how to use the scrolling methods of the <xref:System.Windows.Controls.ScrollViewer> element.</span></span> <span data-ttu-id="6ead2-104">Artımlı içeriğini, çizgi veya sayfası, kaydırma bu yöntemler sağlayan bir <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="6ead2-104">These methods provide incremental scrolling of content, either by line or by page, in a <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ead2-105">Örnek</span><span class="sxs-lookup"><span data-stu-id="6ead2-105">Example</span></span>  
 <span data-ttu-id="6ead2-106">Aşağıdaki örnek, oluşturur bir <xref:System.Windows.Controls.ScrollViewer> adlı `sv1`, bir alt barındıran <xref:System.Windows.Controls.TextBlock> öğesi.</span><span class="sxs-lookup"><span data-stu-id="6ead2-106">The following example creates a <xref:System.Windows.Controls.ScrollViewer> named `sv1`, which hosts a child <xref:System.Windows.Controls.TextBlock> element.</span></span> <span data-ttu-id="6ead2-107">Çünkü <xref:System.Windows.Controls.TextBlock> üst büyük <xref:System.Windows.Controls.ScrollViewer>, kaydırma etkinleştirmek için kaydırma çubukları görünür.</span><span class="sxs-lookup"><span data-stu-id="6ead2-107">Because the <xref:System.Windows.Controls.TextBlock> is larger than the parent <xref:System.Windows.Controls.ScrollViewer>, scroll bars appear in order to enable scrolling.</span></span> <xref:System.Windows.Controls.Button> <span data-ttu-id="6ead2-108">çeşitli kaydırma yöntemleri temsil eden öğeler, ayrı bir soldaki tutturulmuştur <xref:System.Windows.Controls.StackPanel>.</span><span class="sxs-lookup"><span data-stu-id="6ead2-108">elements that represent the various scrolling methods are docked on the left in a separate <xref:System.Windows.Controls.StackPanel>.</span></span> <span data-ttu-id="6ead2-109">Her <xref:System.Windows.Controls.Button> içinde [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] dosya içinde kaydırma davranışını denetleyen ilgili özel bir yöntem çağırır <xref:System.Windows.Controls.ScrollViewer>.</span><span class="sxs-lookup"><span data-stu-id="6ead2-109">Each <xref:System.Windows.Controls.Button> in the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file calls a related custom method that controls scrolling behavior in <xref:System.Windows.Controls.ScrollViewer>.</span></span>  
  
 [!code-xaml[ScrollViewerMethods#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="6ead2-110">Aşağıdaki örnekte <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> ve <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> yöntemleri.</span><span class="sxs-lookup"><span data-stu-id="6ead2-110">The following example uses the <xref:System.Windows.Controls.ScrollViewer.LineUp%2A> and <xref:System.Windows.Controls.ScrollViewer.LineDown%2A> methods.</span></span>  
  
 [!code-csharp[ScrollViewerMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ScrollViewerMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[ScrollViewerMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ScrollViewerMethods/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="6ead2-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6ead2-111">See also</span></span>

- <xref:System.Windows.Controls.ScrollViewer>
- <xref:System.Windows.Controls.StackPanel>
