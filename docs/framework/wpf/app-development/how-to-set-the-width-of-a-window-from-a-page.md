---
title: 'Nasıl yapılır: bir sayfadan bir pencere genişliğini ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- width of windows [WPF], setting from a page
- windows [WPF], setting width from a page
- pages [WPF], setting window width from
ms.assetid: 31601c92-7889-472a-b07e-bf675ad21c92
ms.openlocfilehash: a0ae0e136e0b7f1cd2a2ec56455e14723e8fa306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545998"
---
# <a name="how-to-set-the-width-of-a-window-from-a-page"></a><span data-ttu-id="ee13f-102">Nasıl yapılır: bir sayfadan bir pencere genişliğini ayarlama</span><span class="sxs-lookup"><span data-stu-id="ee13f-102">How to: Set the Width of a Window from a Page</span></span>
<span data-ttu-id="ee13f-103">Bu örnek penceresinden genişliğini ayarlamak nasıl gösterilmektedir bir <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="ee13f-103">This example illustrates how to set the width of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee13f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ee13f-104">Example</span></span>  
 <span data-ttu-id="ee13f-105">A <xref:System.Windows.Controls.Page> ana penceresinin genişliğini ayarlayarak ayarlayabilirsiniz <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span><span class="sxs-lookup"><span data-stu-id="ee13f-105">A <xref:System.Windows.Controls.Page> can set the width of its host window by setting <xref:System.Windows.Controls.Page.WindowWidth%2A>.</span></span> <span data-ttu-id="ee13f-106">Bu özellik tanır <xref:System.Windows.Controls.Page> , onu barındıran pencere türünün açık bilgisine sahip değil.</span><span class="sxs-lookup"><span data-stu-id="ee13f-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ee13f-107">Kullanarak bir pencerenin genişliğini ayarlamak için <xref:System.Windows.Controls.Page.WindowWidth%2A>, <xref:System.Windows.Controls.Page> pencerenin alt öğesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="ee13f-107">To set the width of a window using <xref:System.Windows.Controls.Page.WindowWidth%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowWidthXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowWidthPage.xaml#setpagewindowwidthxaml)]
