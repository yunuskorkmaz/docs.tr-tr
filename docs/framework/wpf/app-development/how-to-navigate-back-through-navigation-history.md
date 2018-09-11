---
title: 'Nasıl yapılır: Gezinme geçmişinde geri gidin'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- history [WPF], navigating back
- navigation [WPF], through navigation history (back)
ms.assetid: 9343234b-d864-441d-b8a7-d895cba80a87
ms.openlocfilehash: 7266c9486524e962a859c34c9be5ab8f6d7bf7d5
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/11/2018
ms.locfileid: "44367920"
---
# <a name="how-to-navigate-back-through-navigation-history"></a><span data-ttu-id="b8be8-102">Nasıl yapılır: Gezinme geçmişinde geri gidin</span><span class="sxs-lookup"><span data-stu-id="b8be8-102">How to: Navigate Back Through Navigation History</span></span>
<span data-ttu-id="b8be8-103">Bu örnekte, nasıl Gezinme geçmişi yeniden girişine gidin gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b8be8-103">This example illustrates how to navigate to entries in back navigation history.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8be8-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b8be8-104">Example</span></span>  
 <span data-ttu-id="b8be8-105">Barındırılan içeriğinden çalışan kodu bir <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> kullanarak <xref:System.Windows.Navigation.NavigationService>, veya [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] Gezinme geçmişi, bir kerede bir girdiye üzerinden geri gidebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="b8be8-105">Code that is running from content that is hosted in a <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame> using <xref:System.Windows.Navigation.NavigationService>, or [!INCLUDE[TLA#tla_iegeneric](../../../../includes/tlasharptla-iegeneric-md.md)] can navigate back through navigation history, one entry at a time.</span></span>  
  
 <span data-ttu-id="b8be8-106">Gezinme geri bir girişi gerektiren ilk olduğunu girişleri geri Gezinme geçmişi içinde inceleyerek denetimi **CanGoBack** gezinme yedeklenmeden önce bir girdi çağırarak özelliği **GoBack** yöntem.</span><span class="sxs-lookup"><span data-stu-id="b8be8-106">Navigating back one entry requires first checking that there are entries in back navigation history, by inspecting the **CanGoBack** property, before navigating back one entry, by calling the **GoBack** method.</span></span> <span data-ttu-id="b8be8-107">Bu, aşağıdaki örnekte gösterilmiştir:</span><span class="sxs-lookup"><span data-stu-id="b8be8-107">This is illustrated in the following example:</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/HomePage.xaml.cs#navigatebackcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateBackCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/homepage.xaml.vb#navigatebackcode)]  
  
 <span data-ttu-id="b8be8-108">**CanGoBack** ve **GoBack** tarafından uygulanan <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, ve <xref:System.Windows.Navigation.NavigationService>.</span><span class="sxs-lookup"><span data-stu-id="b8be8-108">**CanGoBack** and **GoBack** are implemented by <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Frame>, and <xref:System.Windows.Navigation.NavigationService>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8be8-109">Eğer **GoBack**, ve geri Gezinme geçmişi içinde hiç girdi yok bir <xref:System.InvalidOperationException> tetiklenir.</span><span class="sxs-lookup"><span data-stu-id="b8be8-109">If you call **GoBack**, and there are no entries in back navigation history, an <xref:System.InvalidOperationException> is raised.</span></span>
