---
title: Windows Forms ve Yönetilmeyen Uygulamalar
ms.date: 03/30/2017
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
ms.openlocfilehash: c51645fb64f512b5974000f89e8e98f884a7381d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526207"
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="17187-102">Windows Forms ve Yönetilmeyen Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="17187-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="17187-103">Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalarla birlikte çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="17187-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="17187-104">Aşağıdaki bölümlerde Windows Forms uygulamaları ve denetimleri destekleyen ve değil destekleyen senaryoları ve yapılandırmaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="17187-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17187-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="17187-105">In This Section</span></span>  
 [<span data-ttu-id="17187-106">Windows Forms ve Yönetilmeyen Uygulamalara Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="17187-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="17187-107">Yönetilmeyen uygulamalarla çalışma Windows Forms denetimleri uygulayın ve nasıl kullanılacağı hakkında genel bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="17187-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="17187-108">Nasıl yapılır: ShowDialog Yöntemi ile bir Windows Formunu Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="17187-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="17187-109">Nasıl kullanılacağını gösteren kod örneği sağlar <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönetilmeyen bir uygulamada bir Windows formunda çalıştırılacak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="17187-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="17187-110">Nasıl yapılır: Her Windows Formunu Kendi İş Parçacığında Görüntüleyerek COM Birlikte Çalışmasını Destekleme</span><span class="sxs-lookup"><span data-stu-id="17187-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="17187-111">Bir Windows formunu kendi iş parçacığında çalıştırmak üzere gösteren kod örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="17187-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="17187-112">Ayrıca bkz. [izlenecek yol: COM birlikte çalışma destekleme görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="17187-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="17187-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="17187-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="17187-114">Windows Form için ayrı bir iş parçacığı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="17187-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="17187-115">Bir iş parçacığı için ileti döngüsü başlatır.</span><span class="sxs-lookup"><span data-stu-id="17187-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="17187-116">Bir form için yönetilmeyen bir uygulamadan çağrıları sıralar.</span><span class="sxs-lookup"><span data-stu-id="17187-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17187-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="17187-117">Related Sections</span></span>  
 [<span data-ttu-id="17187-118">.NET Framework Bileşenlerini COM'da Gösterme</span><span class="sxs-lookup"><span data-stu-id="17187-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="17187-119">.NET Framework türleri yönetilmeyen uygulamalarda kullanma hakkında genel bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="17187-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
