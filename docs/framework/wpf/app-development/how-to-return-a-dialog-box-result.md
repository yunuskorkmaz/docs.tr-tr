---
title: 'Nasıl yapılır: İletişim Kutusu Sonucu Döndürme'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], returning results
ms.assetid: 4c5cf286-746b-4052-934d-d80cbf8acba3
ms.openlocfilehash: b574a5bbc08d947371837116915c2fc8c13ec81d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006721"
---
# <a name="how-to-return-a-dialog-box-result"></a><span data-ttu-id="86471-102">Nasıl yapılır: İletişim Kutusu Sonucu Döndürme</span><span class="sxs-lookup"><span data-stu-id="86471-102">How to: Return a Dialog Box Result</span></span>
<span data-ttu-id="86471-103">Bu örnekte, iletişim sonucu çağırarak açılan bir pencere için alma işlemi gösterilmektedir <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="86471-103">This example shows how to retrieve the dialog result for a window that is opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86471-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="86471-104">Example</span></span>  
 <span data-ttu-id="86471-105">Bir iletişim kutusu kapanır önce kendi <xref:System.Windows.Window.DialogResult%2A> özelliği ile ayarlanmalıdır bir <xref:System.Nullable%601> <xref:System.Boolean> nasıl kullanıcı iletişim kutusu kapalıyken gösterir.</span><span class="sxs-lookup"><span data-stu-id="86471-105">Before a dialog box closes, its <xref:System.Windows.Window.DialogResult%2A> property should be set with a <xref:System.Nullable%601><xref:System.Boolean> that indicates how the user closed the dialog box.</span></span> <span data-ttu-id="86471-106">Bu değer tarafından döndürülür <xref:System.Windows.Window.ShowDialog%2A> iletişim kutusu nasıl kapatıldığı ve sonuç olarak, sonuç işlemek nasıl belirlemek istemci kodu izin vermek için.</span><span class="sxs-lookup"><span data-stu-id="86471-106">This value is returned by <xref:System.Windows.Window.ShowDialog%2A> to allow client code to determine how the dialog box was closed and, consequently, how to process the result.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86471-107"><xref:System.Windows.Window.DialogResult%2A> bir pencere çağırarak açıldıysa ayarlanabilir <xref:System.Windows.Window.ShowDialog%2A>.</span><span class="sxs-lookup"><span data-stu-id="86471-107"><xref:System.Windows.Window.DialogResult%2A> can only be set if a window was opened by calling <xref:System.Windows.Window.ShowDialog%2A>.</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#getdialogresultcode)]
 [!code-vb[HOWTOWindowManagementSnippets#GetDialogResultCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#getdialogresultcode)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="86471-108">.NET Framework Güvenliği</span><span class="sxs-lookup"><span data-stu-id="86471-108">.NET Framework Security</span></span>  
 <span data-ttu-id="86471-109">Çağırma <xref:System.Windows.Window.ShowDialog%2A> tüm windows ve kısıtlama olmaksızın kullanıcı girdi olaylarını kullanma izni gerektirir.</span><span class="sxs-lookup"><span data-stu-id="86471-109">Calling <xref:System.Windows.Window.ShowDialog%2A> requires permission to use all windows and user input events without restriction.</span></span>
