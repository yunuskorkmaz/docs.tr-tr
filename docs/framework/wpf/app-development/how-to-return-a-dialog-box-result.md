---
title: "Nasıl yapılır: bir iletişim kutusu sonucunu döndürür"
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
helpviewer_keywords: dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d5a1b8cdc0544bfba3f708db40e8b9c593b45b35
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="1f43e-102">Nasıl yapılır: bir iletişim kutusu sonucunu döndürür</span><span class="sxs-lookup"><span data-stu-id="1f43e-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="1f43e-103">Bu örnek çağırarak açılan bir pencere için iletişim sonucu almak nasıl gösterir <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f43e-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f43e-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="1f43e-104">Example</span></span>  
 <span data-ttu-id="1f43e-105">Bir iletişim kutusu kapanmadan önce kendi <xref:System.Windows.Window.DialogResult%2A> özelliği ile ayarlanmalıdır bir <xref:System.Nullable%601> <xref:System.Boolean> nasıl kullanıcı iletişim kutusu kapalı gösterir.</span><span class="sxs-lookup"><span data-stu-id="1f43e-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="1f43e-106">Bu değer tarafından döndürülen <xref:System.Windows.Window.ShowDialog%2A> iletişim kutusunun nasıl kapatıldığını ve sonuç olarak, sonucu işle nasıl belirlemek istemci kodu izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="1f43e-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f43e-107"><xref:System.Windows.Window.DialogResult%2A>yalnızca bir pencere çağırarak açıldıysa ayarlanabilir <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="1f43e-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="1f43e-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="1f43e-108">.NET Framework Security</span></span>  
 <span data-ttu-id="1f43e-109">Çağırma <xref:System.Windows.Window.ShowDialog%2A> tüm windows ve kullanıcı girdi olaylarını kısıtlama olmaksızın kullanma izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="1f43e-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
