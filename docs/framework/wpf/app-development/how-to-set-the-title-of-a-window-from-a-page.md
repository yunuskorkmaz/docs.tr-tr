---
title: "Nasıl yapılır: bir pencere başlık sayfasından ayarlayın"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- windows [WPF], setting title from a page
- title of window [WPF], setting from a page
- pages [WPF], setting window title from
ms.assetid: fecf0d19-3eb6-4f8c-a44f-ff1b6f2b34b3
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 11f33eede479e090a78bffe841d7998e03eab6c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-the-title-of-a-window-from-a-page"></a><span data-ttu-id="5a586-102">Nasıl yapılır: bir pencere başlık sayfasından ayarlayın</span><span class="sxs-lookup"><span data-stu-id="5a586-102">How to: Set the Title of a Window from a Page</span></span>
<span data-ttu-id="5a586-103">Bu örnek, pencere başlığı ayarlamak nasıl gösterir bir <xref:System.Windows.Controls.Page> barındırılır.</span><span class="sxs-lookup"><span data-stu-id="5a586-103">This example shows how to set the title of the window in which a <xref:System.Windows.Controls.Page> is hosted.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a586-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="5a586-104">Example</span></span>  
 <span data-ttu-id="5a586-105">Bir sayfa ayarlayarak barındırma penceresinin başlık değiştirebilirsiniz <xref:System.Windows.Controls.Page.WindowTitle%2A> özellik sözlüğüdür:</span><span class="sxs-lookup"><span data-stu-id="5a586-105">A page can change the title of the window that is hosting it by setting the <xref:System.Windows.Controls.Page.WindowTitle%2A> property, like so:</span></span>  
  
 [!code-xaml[HOWTONavigationSnippets#SetPageWindowTitleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/SetWindowTitlePage.xaml#setpagewindowtitlexaml)]  
  
> [!NOTE]
>  <span data-ttu-id="5a586-106">Ayarı <xref:System.Windows.Controls.Page.Title%2A> bir sayfa özelliğinin değeri, pencere başlığı değiştirmez.</span><span class="sxs-lookup"><span data-stu-id="5a586-106">Setting the <xref:System.Windows.Controls.Page.Title%2A> property of a page does not change the value of the window title.</span></span> <span data-ttu-id="5a586-107">Bunun yerine, <xref:System.Windows.Controls.Page.Title%2A> gezinti geçmişindeki sayfa girdisinin adını belirtir.</span><span class="sxs-lookup"><span data-stu-id="5a586-107">Instead, <xref:System.Windows.Controls.Page.Title%2A> specifies the name of a page entry in navigation history.</span></span>
