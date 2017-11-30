---
title: "Windows Forms ve Yönetilmeyen Uygulamalar"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ActiveX controls [Windows Forms]
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- Windows Forms, interop
ms.assetid: 81bc100c-fa49-4614-85a6-0f7ab59eac8a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8166ab6a69ce9a774e83e6dbc7278a41805f7a83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/22/2017
---
# <a name="windows-forms-and-unmanaged-applications"></a><span data-ttu-id="cfe27-102">Windows Forms ve Yönetilmeyen Uygulamalar</span><span class="sxs-lookup"><span data-stu-id="cfe27-102">Windows Forms and Unmanaged Applications</span></span>
<span data-ttu-id="cfe27-103">Windows Forms uygulamaları ve denetimleri bazı uyarılar ile yönetilmeyen uygulamalarla birlikte çalışabilirler.</span><span class="sxs-lookup"><span data-stu-id="cfe27-103">Windows Forms applications and controls can interoperate with unmanaged applications, with some caveats.</span></span> <span data-ttu-id="cfe27-104">Aşağıdaki bölümlerde Windows Forms uygulamaları ve denetimleri destekleyen ve değil destekleyen senaryoları ve yapılandırmaları açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="cfe27-104">The following sections describe the scenarios and configurations that Windows Forms applications and controls support and those that they do not support.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cfe27-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="cfe27-105">In This Section</span></span>  
 [<span data-ttu-id="cfe27-106">Windows Forms ve yönetilmeyen uygulamalara genel bakış</span><span class="sxs-lookup"><span data-stu-id="cfe27-106">Windows Forms and Unmanaged Applications Overview</span></span>](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)  
 <span data-ttu-id="cfe27-107">Yönetilmeyen uygulamalarla çalışma Windows Forms denetimleri uygulayın ve nasıl kullanılacağı hakkında genel bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="cfe27-107">Offers general information about how to use and implement Windows Forms controls that work with unmanaged applications.</span></span>  
  
 [<span data-ttu-id="cfe27-108">Nasıl yapılır: ShowDialog yöntemi ile bir Windows formunu görüntüleyerek COM birlikte çalışmasını destekleme</span><span class="sxs-lookup"><span data-stu-id="cfe27-108">How to: Support COM Interop by Displaying a Windows Form with the ShowDialog Method</span></span>](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 <span data-ttu-id="cfe27-109">Nasıl kullanılacağını gösteren kod örneği sağlar <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> yönetilmeyen bir uygulamada bir Windows formunda çalıştırılacak yöntemi.</span><span class="sxs-lookup"><span data-stu-id="cfe27-109">Provides a code example that shows how to use the <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> method to run a Windows Form in an unmanaged application.</span></span>  
  
 [<span data-ttu-id="cfe27-110">Nasıl yapılır: her Windows formunu kendi iş parçacığında görüntüleyerek COM birlikte çalışmasını destekleme</span><span class="sxs-lookup"><span data-stu-id="cfe27-110">How to: Support COM Interop by Displaying Each Windows Form on Its Own Thread</span></span>](../../../../docs/framework/winforms/advanced/how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)  
 <span data-ttu-id="cfe27-111">Bir Windows formunu kendi iş parçacığında çalıştırmak üzere gösteren kod örneği sağlar.</span><span class="sxs-lookup"><span data-stu-id="cfe27-111">Provides a code example that shows how to run a Windows Form on its own thread.</span></span>  
  
 <span data-ttu-id="cfe27-112">Ayrıca bkz. [izlenecek yol: COM birlikte çalışma destekleme görüntüleme her Windows formunda ITS kendi iş parçacığı tarafından](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="cfe27-112">Also see [Walkthrough: Supporting COM Interop by Displaying Each Windows Form on Its Own Thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cfe27-113">Başvuru</span><span class="sxs-lookup"><span data-stu-id="cfe27-113">Reference</span></span>  
 <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType>  
 <span data-ttu-id="cfe27-114">Windows Form için ayrı bir iş parçacığı oluşturmak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="cfe27-114">Used to create a separate thread for a Windows Form.</span></span>  
  
 <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType>  
 <span data-ttu-id="cfe27-115">Bir iş parçacığı için ileti döngüsü başlatır.</span><span class="sxs-lookup"><span data-stu-id="cfe27-115">Starts a message loop for a thread.</span></span>  
  
 <xref:System.Windows.Forms.Control.Invoke%2A>  
 <span data-ttu-id="cfe27-116">Bir form için yönetilmeyen bir uygulamadan çağrıları sıralar.</span><span class="sxs-lookup"><span data-stu-id="cfe27-116">Marshals calls from an unmanaged application to a form.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cfe27-117">İlgili Bölümler</span><span class="sxs-lookup"><span data-stu-id="cfe27-117">Related Sections</span></span>  
 [<span data-ttu-id="cfe27-118">.NET Framework bileşenlerini COM'da gösterme</span><span class="sxs-lookup"><span data-stu-id="cfe27-118">Exposing .NET Framework Components to COM</span></span>](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 <span data-ttu-id="cfe27-119">.NET Framework türleri yönetilmeyen uygulamalarda kullanma hakkında genel bilgiler sunar.</span><span class="sxs-lookup"><span data-stu-id="cfe27-119">Offers general information about how to use .NET Framework types in unmanaged applications.</span></span>
