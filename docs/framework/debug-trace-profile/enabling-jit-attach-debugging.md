---
title: JIT-Ekleme Hata Ayıklamayı Etkinleştirme
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: 7adf1316a36d781439d364746fa11795a7fe165a
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217528"
---
# <a name="enabling-jit-attach-debugging"></a><span data-ttu-id="ef5b6-102">JIT-Ekleme Hata Ayıklamayı Etkinleştirme</span><span class="sxs-lookup"><span data-stu-id="ef5b6-102">Enabling JIT-Attach Debugging</span></span>
<span data-ttu-id="ef5b6-103">JıT-Attach hata ayıklaması, hatalar ile ilgili bir hata ayıklayıcıyı bir işleme iliştirirken veya belirli yöntemler veya işlevler tarafından tetikleniyorsa kullanılan tümceciktir.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-103">JIT-attach debugging is the phrase used to describe attaching a debugger to a process when you encounter errors, or it can be triggered by specific methods or functions.</span></span>  
  
 <span data-ttu-id="ef5b6-104">JıT-Attach hata ayıklaması aşağıdaki hata koşulları altında kullanılır:</span><span class="sxs-lookup"><span data-stu-id="ef5b6-104">JIT-attach debugging is used under the following fault conditions:</span></span>  
  
- <span data-ttu-id="ef5b6-105">İşlenmemiş özel durumlar (hem yerel hem de yönetilen kodda).</span><span class="sxs-lookup"><span data-stu-id="ef5b6-105">Unhandled exceptions (in both native and managed code).</span></span>  
  
- <span data-ttu-id="ef5b6-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> Method veya [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) Işlevi (Windows 7 ailesi).</span><span class="sxs-lookup"><span data-stu-id="ef5b6-106"><xref:System.Environment.FailFast%2A?displayProperty=nameWithType> method or [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) function (Windows 7 family).</span></span>  
  
- <span data-ttu-id="ef5b6-107">Çalışma zamanı önemli hataları.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-107">Runtime fatal errors.</span></span>  
  
 <span data-ttu-id="ef5b6-108">JıT-Attach hata ayıklaması, aşağıdaki yöntemler ve işlevlere yapılan çağrılar tarafından da tetiklenir:</span><span class="sxs-lookup"><span data-stu-id="ef5b6-108">JIT-attach debugging is also triggered by calls to the following methods and functions:</span></span>  
  
- <span data-ttu-id="ef5b6-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-109"><xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ef5b6-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-110"><xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> method.</span></span>  
  
- <span data-ttu-id="ef5b6-111">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) Işlevi (Win32).</span><span class="sxs-lookup"><span data-stu-id="ef5b6-111">[DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) function (Win32).</span></span>  
  
 <span data-ttu-id="ef5b6-112">.NET Framework 4 ' den önce, .NET Framework yerel ve yönetilen hata ayıklayıcıların davranışını denetlemek için ayrı kayıt defteri anahtarları sağladı.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-112">Before the .NET Framework 4, the .NET Framework provided separate registry keys to control the behavior of native and managed debuggers.</span></span> <span data-ttu-id="ef5b6-113">.NET Framework 4 ' te başlayarak, Denetim tek bir kayıt defteri anahtarı altında birleştirilir: HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-113">Starting with the .NET Framework 4, control is consolidated under a single registry key: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug.</span></span> <span data-ttu-id="ef5b6-114">Bu anahtar için ayarlayabileceğiniz değerler, bir hata ayıklayıcının çağrılıp çağrılmadığını ve varsa Kullanıcı etkileşimi gerektiren bir iletişim kutusuyla çağrılması gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-114">The values you can set for that key determine whether a debugger is invoked, and, if so, whether it is invoked with a dialog box that requires user interaction.</span></span> <span data-ttu-id="ef5b6-115">Bu kayıt defteri anahtarını ayarlama hakkında daha fazla bilgi için bkz. [otomatik hata ayıklamayı yapılandırma](/windows/win32/debug/configuring-automatic-debugging).</span><span class="sxs-lookup"><span data-stu-id="ef5b6-115">For information about setting this registry key, see [Configuring Automatic Debugging](/windows/win32/debug/configuring-automatic-debugging).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef5b6-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ef5b6-116">See also</span></span>

- [<span data-ttu-id="ef5b6-117">Hata Ayıklama, İzleme ve Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="ef5b6-117">Debugging, Tracing, and Profiling</span></span>](index.md)
- [<span data-ttu-id="ef5b6-118">Görüntüde Hata Ayıklamayı Kolaylaştırma</span><span class="sxs-lookup"><span data-stu-id="ef5b6-118">Making an Image Easier to Debug</span></span>](making-an-image-easier-to-debug.md)
