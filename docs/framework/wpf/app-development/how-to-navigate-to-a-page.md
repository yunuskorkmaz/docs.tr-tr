---
title: 'Nasıl yapılır: Sayfaya Gitme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pages [WPF], navigating to
- navigation [WPF], to page
ms.assetid: 2a556fc0-748b-417f-a58a-0d05a7afb66f
ms.openlocfilehash: c8e808180682bfd97f397d8cadd1e4deafd7eb06
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59141056"
---
# <a name="how-to-navigate-to-a-page"></a><span data-ttu-id="b9282-102">Nasıl yapılır: Sayfaya Gitme</span><span class="sxs-lookup"><span data-stu-id="b9282-102">How to: Navigate to a Page</span></span>
<span data-ttu-id="b9282-103">Bu örnekte, bir sayfa geçtiğiniz için gelen birkaç yolu gösterilmektedir bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="b9282-103">This example illustrates several ways in which a page can be navigated to from a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9282-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b9282-104">Example</span></span>  
 <span data-ttu-id="b9282-105">Mümkünse bir <xref:System.Windows.Navigation.NavigationWindow> aşağıdakilerden birini kullanarak bir sayfaya gidin:</span><span class="sxs-lookup"><span data-stu-id="b9282-105">It is possible for a <xref:System.Windows.Navigation.NavigationWindow> to navigate to a page using one of the following:</span></span>  
  
-   <span data-ttu-id="b9282-106"><xref:System.Windows.Navigation.NavigationWindow.Source%2A> Özelliği.</span><span class="sxs-lookup"><span data-stu-id="b9282-106">The <xref:System.Windows.Navigation.NavigationWindow.Source%2A> property.</span></span>  
  
-   <span data-ttu-id="b9282-107"><xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> Yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b9282-107">The <xref:System.Windows.Navigation.NavigationWindow.Navigate%2A> method.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigatetopagecode)]
 [!code-vb[HOWTONavigationSnippets#NavigateToPageCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigatetopagecode)]  
  
> [!NOTE]
>  [!INCLUDE[TLA#tla_uri#initcap#plural](../../../../includes/tlasharptla-urisharpinitcapsharpplural-md.md)] <span data-ttu-id="b9282-108">mutlak veya göreli olabilir.</span><span class="sxs-lookup"><span data-stu-id="b9282-108">can be either relative or absolute.</span></span> <span data-ttu-id="b9282-109">Daha fazla bilgi için [paketi URI ' WPF'de](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="b9282-109">For more information, see [Pack URIs in WPF](pack-uris-in-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9282-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b9282-110">See also</span></span>

- <xref:System.Windows.Controls.Frame>
- <xref:System.Windows.Controls.Page>
- <xref:System.Windows.Navigation.NavigationService>
