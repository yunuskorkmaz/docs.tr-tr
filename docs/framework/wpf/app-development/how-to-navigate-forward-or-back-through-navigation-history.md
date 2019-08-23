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
ms.openlocfilehash: 76a78debdce14123cc465ac9abf4db906fe0a2df
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961345"
---
# <a name="how-to-navigate-forward-or-back-through-navigation-history"></a><span data-ttu-id="9e5bb-102">Nasıl yapılır: Gezinme Geçmişinde İleriye veya Geriye Doğru Gitme</span><span class="sxs-lookup"><span data-stu-id="9e5bb-102">How to: Navigate Forward or Back Through Navigation History</span></span>
<span data-ttu-id="9e5bb-103">Bu örnek, gezinme geçmişinde girişlerin ileri veya geri nasıl gezindiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-103">This example illustrates how to navigate forward or back to entries in navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e5bb-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="9e5bb-104">Example</span></span>  
 <span data-ttu-id="9e5bb-105">Aşağıdaki konaklardaki içerikten çalıştırılan kod, tek seferde bir giriş olmak üzere gezinti geçmişi ile ileri veya geri gidebilir.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-105">Code that runs from content in the following hosts can navigate forward or back through navigation history, one entry at a time.</span></span>  
  
- <span data-ttu-id="9e5bb-106"><xref:System.Windows.Navigation.NavigationWindow>kullanarak<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="9e5bb-106"><xref:System.Windows.Navigation.NavigationWindow> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="9e5bb-107"><xref:System.Windows.Controls.Frame>kullanarak<xref:System.Windows.Navigation.NavigationService></span><span class="sxs-lookup"><span data-stu-id="9e5bb-107"><xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService></span></span>  
  
- <span data-ttu-id="9e5bb-108">Internet Explorer</span><span class="sxs-lookup"><span data-stu-id="9e5bb-108">Internet Explorer</span></span>  
  
 <span data-ttu-id="9e5bb-109">Bir giriş ileri gidebilmeniz için önce **CanGoForward** özelliğini inceleyerek ileri gezinme geçmişine giriş olup olmadığını kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-109">Before you can navigate forward one entry, you must first check that there are entries in forward navigation history by inspecting the **CanGoForward** property.</span></span> <span data-ttu-id="9e5bb-110">Bir giriş ileri gitmek için **GoForward** yöntemini çağırın.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-110">To navigate forward one entry, you call the **GoForward** method.</span></span> <span data-ttu-id="9e5bb-111">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e5bb-111">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigateforwardcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateForwardCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigateforwardcode)]  
  
 <span data-ttu-id="9e5bb-112">Bir giriş geri gidebilmeniz için önce **CanGoBack** özelliğini inceleyerek geri gezinti geçmişinde girişler olup olmadığını kontrol etmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-112">Before you can navigate back one entry, you must first check that there are entries in back navigation history by inspecting the **CanGoBack** property.</span></span> <span data-ttu-id="9e5bb-113">Bir giriş geri gitmek için **GoBack** metodunu çağırın.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-113">To navigate back one entry, you call the **GoBack** method.</span></span> <span data-ttu-id="9e5bb-114">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="9e5bb-114">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="9e5bb-115">**CanGoForward**, **GoForward**, **CanGoBack**ve **GoBack** <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-115">**CanGoForward**, **GoForward**, **CanGoBack**, and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e5bb-116">**GoForward**çağırır ve ileri gezinme geçmişinde hiç giriş yoksa veya **GoBack**'i çağırırsanız ve geri gezinme geçmişinde hiç giriş yoksa, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="9e5bb-116">If you call **GoForward**, and there are no entries in forward navigation history, or if you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is thrown.</span></span>
