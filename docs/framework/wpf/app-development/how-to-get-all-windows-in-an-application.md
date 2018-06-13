---
title: 'Nasıl yapılır: bir uygulamadaki tüm pencereleri Al'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
ms.openlocfilehash: 476905899f5f7d573a16ba876c72f28ea34bbf9d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545497"
---
# <a name="how-to-get-all-windows-in-an-application"></a><span data-ttu-id="4dd4f-102">Nasıl yapılır: bir uygulamadaki tüm pencereleri Al</span><span class="sxs-lookup"><span data-stu-id="4dd4f-102">How to: Get all Windows in an Application</span></span>
<span data-ttu-id="4dd4f-103">Bu örnek, tüm alma gösterir <xref:System.Windows.Window> bir uygulamadaki nesneler.</span><span class="sxs-lookup"><span data-stu-id="4dd4f-103">This example shows how to get all <xref:System.Windows.Window> objects in an application.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4dd4f-104">Örnek</span><span class="sxs-lookup"><span data-stu-id="4dd4f-104">Example</span></span>  
 <span data-ttu-id="4dd4f-105">Her örneği <xref:System.Windows.Window> nesne görünür olup olmadığını veya değil, bir koleksiyon tarafından yönetilen pencere referansları otomatik olarak eklenir <xref:System.Windows.Application>ve tan açığa çıkarılan <xref:System.Windows.Application.Windows%2A>.</span><span class="sxs-lookup"><span data-stu-id="4dd4f-105">Every instantiated <xref:System.Windows.Window> object, whether visible or not, is automatically added to a collection of window references that is managed by <xref:System.Windows.Application>, and exposed from <xref:System.Windows.Application.Windows%2A>.</span></span>  
  
 <span data-ttu-id="4dd4f-106">Numaralandırmak <xref:System.Windows.Application.Windows%2A> aşağıdaki kodu kullanarak tüm oluşturulan pencereleri almak için:</span><span class="sxs-lookup"><span data-stu-id="4dd4f-106">You can enumerate <xref:System.Windows.Application.Windows%2A> to get all instantiated windows using the following code:</span></span>  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
