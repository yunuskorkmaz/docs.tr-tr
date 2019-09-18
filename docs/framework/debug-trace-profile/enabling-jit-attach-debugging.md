---
title: JIT-Ekleme Hata Ayıklamayı Etkinleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f4d4e2b3806d2c4d84b59e1cd44eb03ab7b278c9
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052833"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="1bacd-102">JIT-Ekleme Hata Ayıklamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="1bacd-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="1bacd-103">JıT-Attach hata ayıklaması, hatalar ile ilgili bir hata ayıklayıcıyı bir işleme iliştirirken veya belirli yöntemler veya işlevler tarafından tetikleniyorsa kullanılan tümceciktir.</span><span class="sxs-lookup"><span data-stu-id="1bacd-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="1bacd-104">JıT-Attach hata ayıklaması aşağıdaki hata koşulları altında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="1bacd-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="1bacd-105">İşlenmemiş özel durumlar (hem yerel hem de yönetilen kodda).</span><span class="sxs-lookup"><span data-stu-id="1bacd-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="1bacd-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType>Method veya [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) Işlevi (Windows 7 ailesi).</span><span class="sxs-lookup"><span data-stu-id="1bacd-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](https://go.microsoft.com/fwlink/?LinkId=182107) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="1bacd-107">Çalışma zamanı önemli hataları.</span><span class="sxs-lookup"><span data-stu-id="1bacd-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="1bacd-108">JıT-Attach hata ayıklaması, aşağıdaki yöntemler ve işlevlere yapılan çağrılar tarafından da tetiklenir:</span><span class="sxs-lookup"><span data-stu-id="1bacd-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="1bacd-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType>yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="1bacd-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="1bacd-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType>yöntemidir.</span><span class="sxs-lookup"><span data-stu-id="1bacd-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="1bacd-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) Işlevi (Win32).</span><span class="sxs-lookup"><span data-stu-id="1bacd-111">[DebugBreak](https://go.microsoft.com/fwlink/?LinkId=182106) function (Win32).</span></span>  
  
 <span data-ttu-id="1bacd-112">.NET Framework 4 ' den önce, .NET Framework yerel ve yönetilen hata ayıklayıcıların davranışını denetlemek için ayrı kayıt defteri anahtarları sağladı.</span><span class="sxs-lookup"><span data-stu-id="1bacd-112">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="1bacd-113">.NET Framework 4 ' te başlayarak, Denetim tek bir kayıt defteri anahtarı altında birleştirilir: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="1bacd-113">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="1bacd-114">Bu anahtar için ayarlayabileceğiniz değerler, bir hata ayıklayıcının çağrılıp çağrılmadığını ve varsa Kullanıcı etkileşimi gerektiren bir iletişim kutusuyla çağrılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="1bacd-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="1bacd-115">Bu kayıt defteri anahtarını ayarlama hakkında daha fazla bilgi için bkz. [otomatik hata ayıklamayı yapılandırma](https://go.microsoft.com/fwlink/?LinkId=181767).</span><span class="sxs-lookup"><span data-stu-id="1bacd-115">For information about setting this registry key, see [Configuring Automatic Debugging](https://go.microsoft.com/fwlink/?LinkId=181767).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bacd-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bacd-116">See also</span></span>

- [<span data-ttu-id="1bacd-117">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="1bacd-117">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="1bacd-118">Görüntüde Hata Ayıklamayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="1bacd-118">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
