---
title: "Nasıl yapılır: bir pencere aç"
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
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6eec13ec1bac864376fcdf5417cc4be68f16dd46
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-open-a-window"></a><span data-ttu-id="1cd1e-102">Nasıl yapılır: bir pencere aç</span><span class="sxs-lookup"><span data-stu-id="1cd1e-102">How to: Open a Window</span></span>
<span data-ttu-id="1cd1e-103">Bu örnek, bir pencere aç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="1cd1e-103">This example shows how to open a window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd1e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1cd1e-104">Example</span></span>  
 <span data-ttu-id="1cd1e-105">Bir pencere oluşturarak açıldığında <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.Show%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="1cd1e-105">A window is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.Show%2A> method.</span></span> <span data-ttu-id="1cd1e-106"><xref:System.Windows.Window.Show%2A>bir pencere açılır ve yeni penceresini kapatmak beklenmeden hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="1cd1e-106"><xref:System.Windows.Window.Show%2A> opens a window and returns immediately without waiting for the new window to close.</span></span> <span data-ttu-id="1cd1e-107">Bu pencere olarak da bilinen türünde bir *kalıcı olmayan* penceresinde ve kullanıcı girişini kısıtlamaz.</span><span class="sxs-lookup"><span data-stu-id="1cd1e-107">This type of window is also known as a *modeless* window, and doesn't restrict user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="1cd1e-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1cd1e-108">.NET Framework Security</span></span>  
 <span data-ttu-id="1cd1e-109">Örnek oluşturma <xref:System.Windows.Window> güvenli olmayan yerel yöntemleri çağırmak için izin gerektirir (bkz: <xref:System.Windows.Window.%23ctor%2A>).</span><span class="sxs-lookup"><span data-stu-id="1cd1e-109">Instantiating <xref:System.Windows.Window> requires permission to call unsafe native methods (see <xref:System.Windows.Window.%23ctor%2A>).</span></span>
