---
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: b7af03197a43976c47b7ddc30346d622e6b97207
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139142"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="71249-102">Silverlight'ta Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="71249-102">Silverlight Debugging</span></span>
<span data-ttu-id="71249-103">Bu bölümdeki konularda, ortak dil çalışma zamanının (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarda hata ayıklamayı desteklemek için sağladığı ortam ve arabirimler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="71249-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="71249-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="71249-104">In This Section</span></span>  
 [<span data-ttu-id="71249-105">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="71249-106">Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="71249-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="71249-107">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="71249-108">[EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan geçerli CLR Continue-Startup olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="71249-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="71249-109">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="71249-110">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71249-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="71249-111">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="71249-112">Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71249-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="71249-113">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="71249-114">Hedef işlemdeki bir CLR yolundan sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71249-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="71249-115">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="71249-116">[CreateVersionStringFromModule işlev](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)işlevinden döndürülen bir CLR sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="71249-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="71249-117">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="71249-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="71249-118">Uzak makinede çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71249-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="71249-119">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="71249-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="71249-120">Uzak makinedeki bir işlemde yüklenen bir CLR örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="71249-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="71249-121">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="71249-122">Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.</span><span class="sxs-lookup"><span data-stu-id="71249-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="71249-123">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71249-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="71249-124">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="71249-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="71249-125">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="71249-126">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="71249-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="71249-127">ShutdownDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="71249-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="71249-128">Uzak hedef makineye bağlantı için taşıma yöneticisini kapatır.</span><span class="sxs-lookup"><span data-stu-id="71249-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71249-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71249-129">See also</span></span>

- [<span data-ttu-id="71249-130">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="71249-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [<span data-ttu-id="71249-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71249-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="71249-132">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="71249-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [<span data-ttu-id="71249-133">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="71249-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="71249-134">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="71249-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
