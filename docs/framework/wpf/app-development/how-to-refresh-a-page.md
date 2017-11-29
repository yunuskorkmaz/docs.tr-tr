---
title: "Nasıl yapılır: bir sayfayı yenileyin"
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
- pages [WPF], refreshing
- refreshing pages [WPF]
ms.assetid: 06dd1bbd-81c4-40ad-ac0d-7a5b326b1465
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d122f6b2ca85724715e18bbc6a00a7104c27bb2d
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-refresh-a-page"></a><span data-ttu-id="070a3-102">Nasıl yapılır: bir sayfayı yenileyin</span><span class="sxs-lookup"><span data-stu-id="070a3-102">How to: Refresh a Page</span></span>
<span data-ttu-id="070a3-103">Bu örnek nasıl çağrılacağını gösterir <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> geçerli içeriği yenilemek için yöntemi bir <xref:System.Windows.Navigation.NavigationWindow>.</span><span class="sxs-lookup"><span data-stu-id="070a3-103">This example shows how to call the <xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> method to refresh the current content in a <xref:System.Windows.Navigation.NavigationWindow>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="070a3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="070a3-104">Example</span></span>  
 <span data-ttu-id="070a3-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A>Geçerli içeriği yeniler bir <xref:System.Windows.Navigation.NavigationWindow> kaynağından yüklenecek.</span><span class="sxs-lookup"><span data-stu-id="070a3-105"><xref:System.Windows.Navigation.NavigationWindow.Refresh%2A> refreshes the current content in a <xref:System.Windows.Navigation.NavigationWindow> to be reloaded from its source.</span></span>  
  
 [!code-csharp[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTONavigationSnippets/CSharp/MainWindow.xaml.cs#navigaterefreshcode)]
 [!code-vb[HOWTONavigationSnippets#NavigateRefreshCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTONavigationSnippets/visualbasic/mainwindow.xaml.vb#navigaterefreshcode)]
