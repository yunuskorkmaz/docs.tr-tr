---
title: "Nasıl yapılır: bir sayfasına gidin"
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
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fa4d0881d7dcdb2c56c66c5617652ec1a2cbc374
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="58bf4-102">Nasıl yapılır: bir sayfasına gidin</span><span class="sxs-lookup"><span data-stu-id="58bf4-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="58bf4-103">Bu örnek, bir sayfa gidilebilecek gelen çeşitli yollar gösterilmektedir bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="58bf4-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58bf4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="58bf4-104">Example</span></span>  
 <span data-ttu-id="58bf4-105">Mümkünse bir <xref:System.Windows.Navigation.NavigationWindow> aşağıdakilerden birini kullanarak bir sayfaya gitmek için:</span><span class="sxs-lookup"><span data-stu-id="58bf4-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
-   <span data-ttu-id="58bf4-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> Özelliği.</span><span class="sxs-lookup"><span data-stu-id="58bf4-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
-   <span data-ttu-id="58bf4-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Yöntemi.</span><span class="sxs-lookup"><span data-stu-id="58bf4-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)]<span data-ttu-id="58bf4-108">göreli veya mutlak olabilir.</span><span class="sxs-lookup"><span data-stu-id="58bf4-108"> can be either relative or absolute.</span></span> <span data-ttu-id="58bf4-109">Daha fazla bilgi için bkz: [Pack URI WPF'de](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="58bf4-109">For more information, see [Pack URIs in WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58bf4-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="58bf4-110">See Also</span></span>  
 <xref:System.Windows.Controls.Frame>  
 <xref:System.Windows.Controls.Page>  
 <xref:System.Windows.Navigation.NavigationService>
