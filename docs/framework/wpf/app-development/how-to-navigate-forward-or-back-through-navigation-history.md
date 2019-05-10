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
ms.openlocfilehash: 00a41fcf85583ec0d081a2fa099f3a77cfcd2900
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625353"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="335eb-102">Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme</span><span class="sxs-lookup"><span data-stu-id="335eb-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="335eb-103">Bu örnek girişleri gezinme geçmişinde ileriye veya geriye gitmek nasıl gösterir.</span><span class="sxs-lookup"><span data-stu-id="335eb-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="335eb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="335eb-104">Example</span></span>  
 <span data-ttu-id="335eb-105">Şu konakları içeriğinden çalışan kod gezinti geçmişinde bir zamanda bir girdi İleri veya geri gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="335eb-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="335eb-106"><xref:System.Windows.Navigation.NavigationWindow> kullanma <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="335eb-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="335eb-107"><xref:System.Windows.Controls.Frame> kullanma <xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="335eb-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)]  
  
 <span data-ttu-id="335eb-108">Bir girdi ileriye gidebilirsiniz önce ilk olduğunu girişleri İleri Gezinme geçmişi içinde inceleyerek işaretlemeniz gerekir **CanGoForward** özelliği.</span><span class="sxs-lookup"><span data-stu-id="335eb-108">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="335eb-109">Bir girdi ileriye gezinmek için çağrı **GoForward** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="335eb-109">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="335eb-110">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="335eb-110">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="335eb-111">Gidebilirsiniz önce bir girdi geri, olduğunu girişleri geri Gezinme geçmişi içinde incelenerek ilk denetlemelisiniz **CanGoBack** özelliği.</span><span class="sxs-lookup"><span data-stu-id="335eb-111">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="335eb-112">Bir girdiye geri gitmek için çağrı **GoBack** yöntemi.</span><span class="sxs-lookup"><span data-stu-id="335eb-112">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="335eb-113">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="335eb-113">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="335eb-114">**CanGoForward**, **GoForward**, **CanGoBack**, ve **GoBack** tarafından uygulanan <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="335eb-114">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="335eb-115">Eğer **GoForward**, ve İleri Gezinme geçmişi içinde hiç girdi yok veya çağırırsanız **GoBack**, ve geri Gezinme geçmişi içinde hiç girdi yok bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="335eb-115">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
