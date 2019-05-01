---
title: 'Nasıl yapılır: Pencere Açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947686"
---
# <a name="how-to-open-a-window"></a><span data-ttu-id="b36aa-102">Nasıl yapılır: Pencere Açma</span><span class="sxs-lookup"><span data-stu-id="b36aa-102">How to: Open a Window</span></span>
<span data-ttu-id="b36aa-103">Bu örnek, bir pencere aç gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="b36aa-103">This example shows how to open a window.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b36aa-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="b36aa-104">Example</span></span>  
 <span data-ttu-id="b36aa-105">Örnekleme tarafından bir pencere açılırsa <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.Show%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b36aa-105">A window is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.Show%2A> method.</span></span> <span data-ttu-id="b36aa-106"><xref:System.Windows.Window.Show%2A> bir pencere açılır ve yeni penceresini kapatmak beklenmeden hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="b36aa-106"><xref:System.Windows.Window.Show%2A> opens a window and returns immediately without waiting for the new window to close.</span></span> <span data-ttu-id="b36aa-107">Bu pencere türü de denir bir *geçici* penceresinde ve kullanıcı girişi kısıtlamaz.</span><span class="sxs-lookup"><span data-stu-id="b36aa-107">This type of window is also known as a *modeless* window, and doesn't restrict user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="b36aa-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="b36aa-108">.NET Framework Security</span></span>  
 <span data-ttu-id="b36aa-109">Örnekleme <xref:System.Windows.Window> güvenli olmayan yerel yöntemleri çağırma izni gerektirir (bkz <xref:System.Windows.Window.%23ctor%2A>).</span><span class="sxs-lookup"><span data-stu-id="b36aa-109">Instantiating <xref:System.Windows.Window> requires permission to call unsafe native methods (see <xref:System.Windows.Window.%23ctor%2A>).</span></span>
