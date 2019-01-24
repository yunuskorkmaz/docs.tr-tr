---
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414526d498b39e894c6bd3530a446f8c06f46378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572753"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="9d747-102">Silverlight'ta Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="9d747-102">Silverlight Debugging</span></span>
<span data-ttu-id="9d747-103">Bu bölümdeki konularda, ortam ve ortak dil çalışma zamanı (CLR), Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamaların hata ayıklama desteği sağlayan arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="9d747-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9d747-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="9d747-104">In This Section</span></span>  
 [<span data-ttu-id="9d747-105">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="9d747-106">Bir işlemde CLRs numaralandırmak için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="9d747-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="9d747-107">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="9d747-108">Bir dizi tarafından döndürülen tanıtıcı bulunan herhangi bir geçerli CLR devam başlangıç olayları kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcı ve dize yolu diziler için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="9d747-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="9d747-109">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="9d747-110">Bir uzak hedef işlemi ve çalışma zamanı numaralandırması için bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d747-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="9d747-111">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="9d747-112">Uzak işlem üzerinde yönetilen hata ayıklama oturumu oluşturmak için işlevsellik sağlar. bir hata ayıklayıcı arabirim oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d747-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="9d747-113">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="9d747-114">Hedef işlemdeki CLR yoldan bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d747-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="9d747-115">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="9d747-116">Sağlayıcıdan döndürülen bir CLR sürüm dizesi kabul eden [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)işlev ve karşılık gelen bir hata ayıklayıcı arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="9d747-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="9d747-117">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="9d747-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="9d747-118">Uzak bir makinede çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d747-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="9d747-119">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="9d747-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="9d747-120">Bir işlem uzak bir makinede yüklü olduğu bir CLR örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="9d747-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="9d747-121">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="9d747-122">Oluşturur veya üzerine belirtilen hedef işlemde yüklenmekte olan tüm ortak dil çalışma zamanı (CLR) tarafından sinyal bir olay işleyici açılır.</span><span class="sxs-lookup"><span data-stu-id="9d747-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="9d747-123">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d747-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="9d747-124">Bir uzak hedef işlemi ve çalışma zamanı numaralandırması için bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="9d747-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="9d747-125">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="9d747-126">İşlem ve çalışma zamanı numaralandırması için bir uzak hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.</span><span class="sxs-lookup"><span data-stu-id="9d747-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="9d747-127">ShutdownDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d747-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="9d747-128">Bağlantı için bir uzak hedef makine aktarım Yöneticisi'ni kapatır.</span><span class="sxs-lookup"><span data-stu-id="9d747-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d747-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d747-129">See also</span></span>
- [<span data-ttu-id="9d747-130">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="9d747-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [<span data-ttu-id="9d747-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="9d747-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="9d747-132">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9d747-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [<span data-ttu-id="9d747-133">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="9d747-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="9d747-134">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="9d747-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
