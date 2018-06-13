---
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80cee666a05432099a380a5ac547a5ca28698c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436039"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="d6496-102">Silverlight'ta Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="d6496-102">Silverlight Debugging</span></span>
<span data-ttu-id="d6496-103">Bu bölümdeki konular, ortam ve ortak dil çalışma zamanı (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarında hata ayıklama desteği sağlayan arabirimler açıklanmaktadır.</span><span class="sxs-lookup"><span data-stu-id="d6496-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d6496-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="d6496-104">In This Section</span></span>  
 [<span data-ttu-id="d6496-105">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-105">EnumerateCLRs Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 <span data-ttu-id="d6496-106">Bir işlemde CLRs numaralandırma için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="d6496-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="d6496-107">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-107">CloseCLREnumeration Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 <span data-ttu-id="d6496-108">İşleyici tarafından döndürülen bir dizi bulunan herhangi bir geçerli CLR devam başlangıç olayı kapatır [EnumerateCLRs işlevi](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)ve tanıtıcısı ve dize yolu diziler için bellek boşaltır.</span><span class="sxs-lookup"><span data-stu-id="d6496-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="d6496-109">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-109">CreateCoreClrDebugTarget Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="d6496-110">İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef için bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6496-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="d6496-111">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-111">CreateCordbObject Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 <span data-ttu-id="d6496-112">Yönetilen hata ayıklama oturumu uzak bir işlem üzerinde başlatmasını için işlevsellik sağlayan bir hata ayıklayıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6496-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="d6496-113">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-113">CreateVersionStringFromModule Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 <span data-ttu-id="d6496-114">Bir hedef işlemde CLR yolundan bir sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6496-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="d6496-115">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-115">CreateDebuggingInterfaceFromVersion Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="d6496-116">Bir CLR sürüm dizesi döndürdü kabul [CreateVersionStringFromModule işlevi](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)işlev ve karşılık gelen bir hata ayıklayıcı arabirimini döndürür.</span><span class="sxs-lookup"><span data-stu-id="d6496-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="d6496-117">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="d6496-117">CoreClrDebugProcInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="d6496-118">Uzak makinede çalışan bir işlemin temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6496-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="d6496-119">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="d6496-119">CoreClrDebugRuntimeInfo Structure</span></span>](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="d6496-120">Bir işlemde bir uzak makinede yüklü bir CLR örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="d6496-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="d6496-121">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-121">GetStartupNotificationEvent Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 <span data-ttu-id="d6496-122">Sonra belirtilen hedef işleminde yüklenen tüm ortak dil çalışma zamanı (CLR) tarafından bildirim yapılan bir olay tanıtıcısı açar veya oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6496-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="d6496-123">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6496-123">ICoreClrDebugTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="d6496-124">İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef için bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="d6496-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="d6496-125">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-125">InitDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 <span data-ttu-id="d6496-126">İşlem ve çalışma zamanı numaralandırması için uzaktan bir hedef bağlanmak için Aktarım Yöneticisi'ni başlatır.</span><span class="sxs-lookup"><span data-stu-id="d6496-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="d6496-127">ShutdownDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6496-127">ShutdownDbgTransportManager Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="d6496-128">Bağlantı uzak hedef makine için Aktarım Yöneticisi'ni kapatır.</span><span class="sxs-lookup"><span data-stu-id="d6496-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6496-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d6496-129">See Also</span></span>  
 [<span data-ttu-id="d6496-130">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="d6496-130">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [<span data-ttu-id="d6496-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d6496-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="d6496-132">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d6496-132">Debugging Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [<span data-ttu-id="d6496-133">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="d6496-133">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="d6496-134">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="d6496-134">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
