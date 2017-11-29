---
title: "Silverlight'ta Hata Ayıklama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: bf39d2dd12207d594c7bf5bd5b249d82c3f15d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="silverlight-debugging"></a><span data-ttu-id="eca68-102">Silverlight'ta Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="eca68-102">Silverlight Debugging</span></span>
<span data-ttu-id="eca68-103">Bu bölümdeki konular, ortam ve ortak dil çalışma zamanı (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarında hata ayıklama desteği sağlayan arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="eca68-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eca68-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="eca68-104">In This Section</span></span>  
 [<span data-ttu-id="eca68-105">EnumerateCLRs işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="eca68-106">Bir işlemde CLRs numaralandırma için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="eca68-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="eca68-107">CloseCLREnumeration işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="eca68-108">İşleyici tarafından döndürülen bir dizi bulunan herhangi bir geçerli CLR devam başlangıç olayı kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcısı ve dize yolu diziler için bellek boşaltır.</span><span class="sxs-lookup"><span data-stu-id="eca68-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="eca68-109">CreateCoreClrDebugTarget işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="eca68-110">İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef için bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eca68-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="eca68-111">CreateCordbObject işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="eca68-112">Yönetilen hata ayıklama oturumu uzak bir işlem üzerinde başlatmasını için işlevsellik sağlayan bir hata ayıklayıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eca68-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="eca68-113">CreateVersionStringFromModule işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="eca68-114">Bir hedef işlemde CLR yolundan bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eca68-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="eca68-115">Createdebuggingınterfacefromversion işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="eca68-116">Bir CLR sürüm dizesi döndürdü kabul [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)işlev ve karşılık gelen bir hata ayıklayıcı arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="eca68-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="eca68-117">Coreclrdebugprocınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="eca68-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="eca68-118">Uzak makinede çalışan bir işlemin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eca68-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="eca68-119">Coreclrdebugruntimeınfo yapısı</span><span class="sxs-lookup"><span data-stu-id="eca68-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="eca68-120">Bir işlemde bir uzak makinede yüklü bir CLR örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="eca68-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="eca68-121">GetStartupNotificationEvent işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="eca68-122">Sonra belirtilen hedef işleminde yüklenen tüm ortak dil çalışma zamanı (CLR) tarafından bildirim yapılan bir olay tanıtıcısı açar veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eca68-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="eca68-123">Icoreclrdebugtarget arabirimi</span><span class="sxs-lookup"><span data-stu-id="eca68-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="eca68-124">İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef için bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="eca68-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="eca68-125">Initdbgtransportmanager işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="eca68-126">İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.</span><span class="sxs-lookup"><span data-stu-id="eca68-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="eca68-127">ShutdownDbgTransportManager işlevi</span><span class="sxs-lookup"><span data-stu-id="eca68-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="eca68-128">Bağlantı uzak hedef makine için Aktarım Yöneticisi'ni kapatır.</span><span class="sxs-lookup"><span data-stu-id="eca68-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca68-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eca68-129">See Also</span></span>  
 [<span data-ttu-id="eca68-130">Hata ayıklama coclass'ları</span><span class="sxs-lookup"><span data-stu-id="eca68-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [<span data-ttu-id="eca68-131">Hata ayıklama arabirimleri</span><span class="sxs-lookup"><span data-stu-id="eca68-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="eca68-132">Hata ayıklama genel statik işlevleri</span><span class="sxs-lookup"><span data-stu-id="eca68-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [<span data-ttu-id="eca68-133">Hata ayıklama numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="eca68-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="eca68-134">Hata ayıklama yapıları</span><span class="sxs-lookup"><span data-stu-id="eca68-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
