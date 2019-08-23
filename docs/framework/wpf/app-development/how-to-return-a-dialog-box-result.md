---
title: 'Nasıl yapılır: İletişim Kutusu Sonucu Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: 5e3670006762bcd09634b29314ecf2d05b1a44da
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968240"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="113fc-102">Nasıl yapılır: İletişim Kutusu Sonucu Döndürme</span><span class="sxs-lookup"><span data-stu-id="113fc-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="113fc-103">Bu örnek, çağırarak <xref:System.Windows.Window.ShowDialog%2A>açılan bir pencere için diyalog sonucunun nasıl alınacağını gösterir.</span><span class="sxs-lookup"><span data-stu-id="113fc-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="113fc-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="113fc-104">Example</span></span>  
 <span data-ttu-id="113fc-105">İletişim kutusu kapanmadan önce, <xref:System.Windows.Window.DialogResult%2A> özelliği kullanıcının iletişim kutusunu nasıl kapattığını gösteren bir <xref:System.Nullable%601> <xref:System.Boolean> ile ayarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="113fc-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="113fc-106">Bu değer, istemci kodunun <xref:System.Windows.Window.ShowDialog%2A> iletişim kutusunun nasıl kapatıldığını ve sonuç olarak sonucun nasıl işleyeceğini belirlemesine izin vermek için tarafından döndürülür.</span><span class="sxs-lookup"><span data-stu-id="113fc-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="113fc-107"><xref:System.Windows.Window.DialogResult%2A>yalnızca, çağırarak <xref:System.Windows.Window.ShowDialog%2A>bir pencere açılırsa ayarlanabilir.</span><span class="sxs-lookup"><span data-stu-id="113fc-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="113fc-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="113fc-108">.NET Framework Security</span></span>  
 <span data-ttu-id="113fc-109">Çağırma <xref:System.Windows.Window.ShowDialog%2A> , tüm Windows ve Kullanıcı giriş olaylarını kısıtlama olmadan kullanma izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="113fc-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
