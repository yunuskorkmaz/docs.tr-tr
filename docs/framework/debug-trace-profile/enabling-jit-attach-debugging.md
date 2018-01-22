---
title: "JIT-Ekleme Hata Ayıklamayı Etkinleştirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71b2e95076edbda3a67a84c9185d8b689c158e12
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="f20f6-102">JIT-Ekleme Hata Ayıklamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f20f6-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="f20f6-103">JIT-ekleme hata ayıklama hatalarla ya da belirli yöntemler ve işlevlere tarafından tetiklenebilir bir hata ayıklayıcısı bir işlemine iliştirme tanımlamak için kullanılan terimdir.</span><span class="sxs-lookup"><span data-stu-id="f20f6-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="f20f6-104">JIT-ekleme hata ayıklama, aşağıdaki hata koşullar altında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="f20f6-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
-   <span data-ttu-id="f20f6-105">İşlenmemiş özel durumlardan (yerel ve yönetilen kod).</span><span class="sxs-lookup"><span data-stu-id="f20f6-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
-   <span data-ttu-id="f20f6-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>yöntem veya [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) işlevi (Windows 7 ailesi).</span><span class="sxs-lookup"><span data-stu-id="f20f6-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](http://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
-   <span data-ttu-id="f20f6-107">Çalışma zamanı önemli hataları.</span><span class="sxs-lookup"><span data-stu-id="f20f6-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="f20f6-108">JIT-ekleme hata ayıklama işlevleri ve aşağıdaki yöntemlerden yapılan çağrılar tarafından da tetiklenir:</span><span class="sxs-lookup"><span data-stu-id="f20f6-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
-   <span data-ttu-id="f20f6-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>yöntem.</span><span class="sxs-lookup"><span data-stu-id="f20f6-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="f20f6-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>yöntem.</span><span class="sxs-lookup"><span data-stu-id="f20f6-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="f20f6-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) işlevi (Win32).</span><span class="sxs-lookup"><span data-stu-id="f20f6-111">[DebugBreak](http://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="f20f6-112">Önce [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], .NET Framework yerel ve yönetilen hata ayıklayıcıları davranışını denetlemek için ayrı kayıt defteri anahtarlarını sağlanan.</span><span class="sxs-lookup"><span data-stu-id="f20f6-112">Before the [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="f20f6-113">İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], denetimi altında bir tek kayıt defteri anahtarını birleştirilmiş: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="f20f6-113">Starting with the [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="f20f6-114">Bu anahtar için ayarlayabileceğiniz değerler bir hata ayıklayıcısı çağrılır, ve olup kullanıcı etkileşimi gerektiren bir iletişim kutusuyla çağrılması gerekiyorsa, olup olmadığını belirler.</span><span class="sxs-lookup"><span data-stu-id="f20f6-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="f20f6-115">Bu kayıt defteri anahtarı ayarlama hakkında daha fazla bilgi için bkz: [otomatik hata ayıklama yapılandırma](http://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="f20f6-115">For information about setting this registry key, see [Configuring Automatic Debugging](http://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f20f6-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f20f6-116">See Also</span></span>  
 [<span data-ttu-id="f20f6-117">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f20f6-117">Debugging, Tracing, and Profiling</span></span>](../../../docs/framework/debug-trace-profile/index.md)  
 [<span data-ttu-id="f20f6-118">Görüntüde Hata Ayıklamayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="f20f6-118">Making an Image Easier to Debug</span></span>](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 [<span data-ttu-id="f20f6-119">Profil oluşturma etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="f20f6-119">Enabling Profiling</span></span>](http://msdn.microsoft.com/library/3b669676-f0e0-4ebf-8674-68986dd2020d)
