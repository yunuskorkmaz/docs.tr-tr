---
title: 'Nasıl yapılır: İletişim Kutusu Açma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 70ac31285dd22244b4bd6ad0d188d182eb6e6264
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59084993"
---
# <a name="how-to-open-a-dialog-box"></a><span data-ttu-id="ce4d4-102">Nasıl yapılır: İletişim Kutusu Açma</span><span class="sxs-lookup"><span data-stu-id="ce4d4-102">How to: Open a Dialog Box</span></span>
<span data-ttu-id="ce4d4-103">Bu örnek, bir iletişim kutusunu açmak gösterilmektedir.</span><span class="sxs-lookup"><span data-stu-id="ce4d4-103">This example shows how to open a dialog box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce4d4-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="ce4d4-104">Example</span></span>  
 <span data-ttu-id="ce4d4-105">Bir iletişim kutusu örneği tarafından açılan bir penceredir <xref:System.Windows.Window> ve çağırma <xref:System.Windows.Window.ShowDialog%2A> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ce4d4-105">A dialog box is a window that is opened by instantiating <xref:System.Windows.Window> and calling the <xref:System.Windows.Window.ShowDialog%2A> method.</span></span> <span data-ttu-id="ce4d4-106"><xref:System.Windows.Window.ShowDialog%2A> bir pencere açılır ve yeni iletişim kutusu kapatıldı kadar döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="ce4d4-106"><xref:System.Windows.Window.ShowDialog%2A> opens a window and doesn't return until the new dialog box has been closed.</span></span> <span data-ttu-id="ce4d4-107">Bu pencere türü olarak da bilinen olduğu bir *kalıcı* penceresinde ve kullanıcı girişini kısıtlayan.</span><span class="sxs-lookup"><span data-stu-id="ce4d4-107">This type of window is also known as a *modal* window, and restricts user input.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="ce4d4-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="ce4d4-108">.NET Framework Security</span></span>  
 <span data-ttu-id="ce4d4-109">Çağırma <xref:System.Windows.Window.ShowDialog%2A> tüm windows ve kısıtlama olmaksızın kullanıcı girdi olaylarını kullanma izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="ce4d4-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce4d4-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce4d4-110">See also</span></span>

- [<span data-ttu-id="ce4d4-111">İletişim Kutusu Sonucu Döndürme</span><span class="sxs-lookup"><span data-stu-id="ce4d4-111">Return a Dialog Box Result</span></span>](how-to-return-a-dialog-box-result.md)
