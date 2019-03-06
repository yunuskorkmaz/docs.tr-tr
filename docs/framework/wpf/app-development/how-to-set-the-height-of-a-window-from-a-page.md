---
title: 'Nasıl yapılır: Bir sayfadan pencere yüksekliğini ayarlama'
ms.date: 03/30/2017
helpviewer_keywords:
- windows [WPF], setting height from a page
- pages [WPF], setting window height from
- height of window [WPF], setting from a page
ms.assetid: 4e4488ff-ab5c-4ee9-81a4-e1addb55c5cc
ms.openlocfilehash: c99ea134478635f368b71443f43e4d8f772cb5aa
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370984"
---
# <a name="how-to-set-the-height-of-a-window-from-a-page"></a><span data-ttu-id="bd992-102">Nasıl yapılır: Bir sayfadan pencere yüksekliğini ayarlama</span><span class="sxs-lookup"><span data-stu-id="bd992-102">How to: Set the Height of a Window from a Page</span></span>
<span data-ttu-id="bd992-103">Bu örnekte pencere yüksekliğini ayarlama bir <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="bd992-103">This example illustrates how to set the height of the window from a <xref:System.Windows.Controls.Page>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd992-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="bd992-104">Example</span></span>  
 <span data-ttu-id="bd992-105">A <xref:System.Windows.Controls.Page> konak penceresinin yüksekliğini ayarlayarak ayarlayabilirsiniz <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span><span class="sxs-lookup"><span data-stu-id="bd992-105">A <xref:System.Windows.Controls.Page> can set the height of its host window by setting <xref:System.Windows.Controls.Page.WindowHeight%2A>.</span></span> <span data-ttu-id="bd992-106">Bu özellik tanır <xref:System.Windows.Controls.Page> barındırdığı penceresini açık bilgisi almamayı.</span><span class="sxs-lookup"><span data-stu-id="bd992-106">This property allows the <xref:System.Windows.Controls.Page> to not have explicit knowledge of the type of window that hosts it.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bd992-107">Kullanarak bir pencerenin yüksekliğini ayarlamak için <xref:System.Windows.Controls.Page.WindowHeight%2A>, <xref:System.Windows.Controls.Page> pencerenin alt öğesi olması gerekir.</span><span class="sxs-lookup"><span data-stu-id="bd992-107">To set the height of a window using <xref:System.Windows.Controls.Page.WindowHeight%2A>, a <xref:System.Windows.Controls.Page> must be the child of a window.</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowHeightXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowHeightPage.xaml#setpagewindowheightxaml)]
