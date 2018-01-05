---
title: "Nasıl yapılır: bir iletişim kutusu açın"
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
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e6201b7dbcc57a15583b7d95d6b603ab50e951a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="43e0d-102">Nasıl yapılır: bir iletişim kutusu açın</span><span class="sxs-lookup"><span data-stu-id="43e0d-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="43e0d-103">Bu örnek, bir iletişim kutusunu açmak gösterilmiştir.</span><span class="sxs-lookup"><span data-stu-id="43e0d-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43e0d-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="43e0d-104">Example</span></span>  
 <span data-ttu-id="43e0d-105">Bir iletişim kutusu örneği tarafından açılan bir penceredir <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="43e0d-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="43e0d-106"><xref:System.Windows.Window.ShowDialog%2A>bir pencere açılır ve yeni iletişim kutusu kapatılana kadar döndürmez.</span><span class="sxs-lookup"><span data-stu-id="43e0d-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="43e0d-107">Bu pencere olarak da bilinen türünde bir *kalıcı* penceresinde ve kullanıcı girişini kısıtlar.</span><span class="sxs-lookup"><span data-stu-id="43e0d-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="43e0d-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="43e0d-108">.NET Framework Security</span></span>  
 <span data-ttu-id="43e0d-109">Çağırma <xref:System.Windows.Window.ShowDialog%2A> tüm windows ve kullanıcı girdi olaylarını kısıtlama olmaksızın kullanma izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="43e0d-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43e0d-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="43e0d-110">See Also</span></span>  
 [<span data-ttu-id="43e0d-111">İletişim Kutusu Sonucu Döndürme</span><span class="sxs-lookup"><span data-stu-id="43e0d-111">Return a Dialog Box Result</span></span>](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
