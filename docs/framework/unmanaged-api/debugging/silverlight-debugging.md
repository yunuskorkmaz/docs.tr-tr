---
description: 'Hakkında daha fazla bilgi edinin: Silverlight hata ayıklaması'
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 54a3f7f4b2de867509ff94dafa25c067a78b3ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800545"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="8c820-103">Silverlight'ta Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="8c820-103">Silverlight Debugging</span></span>

<span data-ttu-id="8c820-104">Bu bölümdeki konularda, ortak dil çalışma zamanının (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarda hata ayıklamayı desteklemek için sağladığı ortam ve arabirimler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="8c820-104">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8c820-105">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="8c820-105">In This Section</span></span>  

 [<span data-ttu-id="8c820-106">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-106">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="8c820-107">Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="8c820-107">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="8c820-108">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-108">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="8c820-109">[EnumerateCLRs işlevi](enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan geçerli CLR Continue-Startup olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="8c820-109">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="8c820-110">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-110">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="8c820-111">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c820-111">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="8c820-112">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-112">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="8c820-113">Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c820-113">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="8c820-114">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-114">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="8c820-115">Hedef işlemdeki bir CLR yolundan sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c820-115">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="8c820-116">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-116">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="8c820-117">[CreateVersionStringFromModule işlev](createversionstringfrommodule-function.md)işlevinden döndürülen bir CLR sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="8c820-117">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="8c820-118">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="8c820-118">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="8c820-119">Uzak makinede çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8c820-119">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="8c820-120">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="8c820-120">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="8c820-121">Uzak makinedeki bir işlemde yüklenen bir CLR örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="8c820-121">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="8c820-122">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-122">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="8c820-123">Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.</span><span class="sxs-lookup"><span data-stu-id="8c820-123">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="8c820-124">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c820-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="8c820-125">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="8c820-125">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="8c820-126">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-126">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="8c820-127">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="8c820-127">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="8c820-128">ShutdownDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="8c820-128">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="8c820-129">Uzak hedef makineye bağlantı için taşıma yöneticisini kapatır.</span><span class="sxs-lookup"><span data-stu-id="8c820-129">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c820-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c820-130">See also</span></span>

- [<span data-ttu-id="8c820-131">Hata Ayıklama Yardımcı Sınıfları</span><span class="sxs-lookup"><span data-stu-id="8c820-131">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="8c820-132">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8c820-132">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8c820-133">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="8c820-133">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="8c820-134">Hata Ayıklama Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="8c820-134">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="8c820-135">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="8c820-135">Debugging Structures</span></span>](debugging-structures.md)
