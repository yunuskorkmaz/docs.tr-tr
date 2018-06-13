---
title: 'Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating forward
- navigation [WPF], through navigation history (forward)
ms.assetid: 5939d574-5f53-469e-85f5-1f2b13607caa
ms.openlocfilehash: ac3b8b71b6adf04d71cf35edbb042b82c57d8e1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33546272"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="7ed7d-102">Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme</span><span class="sxs-lookup"><span data-stu-id="7ed7d-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="7ed7d-103">Bu örnek, Gezinme geçmişi girişlerinde İleri veya geri gitmek göstermektedir.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ed7d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="7ed7d-104">Example</span></span>  
 <span data-ttu-id="7ed7d-105">Şu konakları içerikten çalışan kod, gezinti geçmişinde bir kerede bir girdiye ileriye veya geriye gidebilir.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
-   <span data-ttu-id="7ed7d-106"><xref:System.Windows.Navigation.NavigationWindow> Kullanma <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="7ed7d-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   <span data-ttu-id="7ed7d-107"><xref:System.Windows.Controls.Frame> Kullanma <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="7ed7d-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
-   [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="7ed7d-108">Bir girdi ileriye gidebilirsiniz önce ilk olduğunu girişleri İleri gezinti geçmişinde inceleyerek işaretlemeniz gerekir **CanGoForward** özelliği.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="7ed7d-109">Bir girdi ileriye gitmek için arama **GoForward** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="7ed7d-110">Bu aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7ed7d-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="7ed7d-111">Gezinmek önce bir giriş yeniden, olduğunu girişleri geri gezinti geçmişinde incelenerek ilk denetlemelisiniz **CanGoBack** özelliği.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="7ed7d-112">Bir girdiye geri gitmek için arama **GoBack** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="7ed7d-113">Bu aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="7ed7d-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="7ed7d-114">**CanGoForward**, **GoForward**, **CanGoBack**, ve **GoBack** tarafından uygulanan <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7ed7d-115">Çağırırsanız **GoForward**, ve İleri gezinti geçmişinde hiçbir girdi yoksa veya çağırırsanız **GoBack**, ve geri gezinti geçmişinde hiçbir girdi yoksa bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="7ed7d-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
