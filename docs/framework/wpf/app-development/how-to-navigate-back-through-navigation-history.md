---
title: 'Nasıl yapılır: Gezinme Geçmişinde Geriye Doğru Gitme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 53b32e145390d7052262042c7a793699c163b373
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969348"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="bd90d-102">Nasıl yapılır: Gezinme Geçmişinde Geriye Doğru Gitme</span><span class="sxs-lookup"><span data-stu-id="bd90d-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="bd90d-103">Bu örnek, geri gezinme geçmişindeki girişlere nasıl gidileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bd90d-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd90d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd90d-104">Example</span></span>  
 <span data-ttu-id="bd90d-105"><xref:System.Windows.Navigation.NavigationWindow> ,<xref:System.Windows.Navigation.NavigationService>, Veya Internet Explorer 'da barındırılan içerikten çalıştırılan kod, tek seferde bir giriş olan gezinti geçmişi aracılığıyla geri gidebilir. <xref:System.Windows.Controls.Frame></span><span class="sxs-lookup"><span data-stu-id="bd90d-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or Internet Explorer can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="bd90d-106">Tek bir girdinin geri dönmesi için, önce bir giriş geri gidilerek **CanGoBack** özelliğini Inceleyerek, **GoBack** metodunu çağırarak, geri gezinti geçmişinde girişler olup olmadığını kontrol edin.</span><span class="sxs-lookup"><span data-stu-id="bd90d-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="bd90d-107">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="bd90d-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="bd90d-108">**CanGoBack** ve **GoBack** , <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationWindow> <xref:System.Windows.Navigation.NavigationService>tarafından uygulanır.</span><span class="sxs-lookup"><span data-stu-id="bd90d-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bd90d-109">**GoBack**'i çağırırsanız ve geri gezinme geçmişinde hiç giriş yoksa, bir <xref:System.InvalidOperationException> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="bd90d-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
