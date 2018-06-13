---
title: 'Nasıl yapılır: bir pencere aç'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 23dc74666d8f47a0fb735d96ad22ed56c96bdbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545470"
---
# <a name="how-to-open-a-window"></a><span data-ttu-id="ef1c3-102">Nasıl yapılır: bir pencere aç</span><span class="sxs-lookup"><span data-stu-id="ef1c3-102">How to: Open a Window</span></span>
<span data-ttu-id="ef1c3-103">Bu örnek, bir pencere aç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ef1c3-103">This example shows how to open a window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ef1c3-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ef1c3-104">Example</span></span>  
 <span data-ttu-id="ef1c3-105">Bir pencere oluşturarak açıldığında <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.Show%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ef1c3-105">A window is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.Show%2A> method.</span></span> <span data-ttu-id="ef1c3-106"><xref:System.Windows.Window.Show%2A> bir pencere açılır ve yeni penceresini kapatmak beklenmeden hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="ef1c3-106"><xref:System.Windows.Window.Show%2A> opens a window and returns immediately without waiting for the new window to close.</span></span> <span data-ttu-id="ef1c3-107">Bu pencere olarak da bilinen türünde bir *kalıcı olmayan* penceresinde ve kullanıcı girişini kısıtlamaz.</span><span class="sxs-lookup"><span data-stu-id="ef1c3-107">This type of window is also known as a *modeless* window, and doesn't restrict user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="ef1c3-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ef1c3-108">.NET Framework Security</span></span>  
 <span data-ttu-id="ef1c3-109">Örnek oluşturma <xref:System.Windows.Window> güvenli olmayan yerel yöntemleri çağırmak için izin gerektirir (bkz: <xref:System.Windows.Window.%23ctor%2A>).</span><span class="sxs-lookup"><span data-stu-id="ef1c3-109">Instantiating <xref:System.Windows.Window> requires permission to call unsafe native methods (see <xref:System.Windows.Window.%23ctor%2A>).</span></span>
