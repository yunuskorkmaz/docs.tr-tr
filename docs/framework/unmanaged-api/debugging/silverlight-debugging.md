---
title: Silverlight'ta Hata Ayıklama
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790319"
---
# <a name="silverlight-debugging"></a><span data-ttu-id="c3a40-102">Silverlight'ta Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="c3a40-102">Silverlight Debugging</span></span>
<span data-ttu-id="c3a40-103">Bu bölümdeki konularda, ortak dil çalışma zamanının (CLR) Windows işletim sisteminde veya Macintosh platformunda çalışan Silverlight tabanlı uygulamalarda hata ayıklamayı desteklemek için sağladığı ortam ve arabirimler açıklanır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-103">The topics in this section describe the environment and interfaces that the common language runtime (CLR) provides to support debugging Silverlight-based applications that are running on the Windows operating system, or on the Macintosh platform.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="c3a40-104">Bu Bölümde</span><span class="sxs-lookup"><span data-stu-id="c3a40-104">In This Section</span></span>  
 [<span data-ttu-id="c3a40-105">EnumerateCLRs İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-105">EnumerateCLRs Function</span></span>](enumerateclrs-function.md)  
 <span data-ttu-id="c3a40-106">Bir işlemdeki CLRs 'yi listelemek için bir mekanizma sağlar.</span><span class="sxs-lookup"><span data-stu-id="c3a40-106">Provides a mechanism for enumerating the CLRs in a process.</span></span>  
  
 [<span data-ttu-id="c3a40-107">CloseCLREnumeration İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-107">CloseCLREnumeration Function</span></span>](closeclrenumeration-function.md)  
 <span data-ttu-id="c3a40-108">[EnumerateCLRs işlevi](enumerateclrs-function.md)tarafından döndürülen bir dizi tanıtıcıda bulunan geçerli CLR Continue-Startup olaylarını kapatır ve tanıtıcı ve dize yolu dizileri için belleği serbest bırakır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-108">Closes any valid CLR continue-startup events located in an array of handles returned by the [EnumerateCLRs Function](enumerateclrs-function.md), and frees the memory for the handle and string path arrays.</span></span>  
  
 [<span data-ttu-id="c3a40-109">CreateCoreClrDebugTarget İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-109">CreateCoreClrDebugTarget Function</span></span>](createcoreclrdebugtarget-function.md)  
 <span data-ttu-id="c3a40-110">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3a40-110">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="c3a40-111">CreateCordbObject İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-111">CreateCordbObject Function</span></span>](createcordbobject-function.md)  
 <span data-ttu-id="c3a40-112">Uzak bir işlemde yönetilen bir hata ayıklama oturumunun örneğini oluşturma işlevselliği sağlayan bir hata ayıklayıcı arabirimi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3a40-112">Creates a debugger interface that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
 [<span data-ttu-id="c3a40-113">CreateVersionStringFromModule İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-113">CreateVersionStringFromModule Function</span></span>](createversionstringfrommodule-function.md)  
 <span data-ttu-id="c3a40-114">Hedef işlemdeki bir CLR yolundan sürüm dizesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3a40-114">Creates a version string from a CLR path in a target process.</span></span>  
  
 [<span data-ttu-id="c3a40-115">CreateDebuggingInterfaceFromVersion İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-115">CreateDebuggingInterfaceFromVersion Function</span></span>](createdebugginginterfacefromversion-function-for-silverlight.md)  
 <span data-ttu-id="c3a40-116">[CreateVersionStringFromModule işlev](createversionstringfrommodule-function.md)işlevinden döndürülen bir CLR sürüm dizesini kabul eder ve karşılık gelen bir hata ayıklayıcı arabirimi döndürür.</span><span class="sxs-lookup"><span data-stu-id="c3a40-116">Accepts a CLR version string returned from [CreateVersionStringFromModule Function](createversionstringfrommodule-function.md)function, and returns a corresponding debugger interface.</span></span>  
  
 [<span data-ttu-id="c3a40-117">CoreClrDebugProcInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="c3a40-117">CoreClrDebugProcInfo Structure</span></span>](coreclrdebugprocinfo-structure.md)  
 <span data-ttu-id="c3a40-118">Uzak makinede çalışan bir işlemi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3a40-118">Represents a process that is running on a remote machine.</span></span>  
  
 [<span data-ttu-id="c3a40-119">CoreClrDebugRuntimeInfo Yapısı</span><span class="sxs-lookup"><span data-stu-id="c3a40-119">CoreClrDebugRuntimeInfo Structure</span></span>](coreclrdebugruntimeinfo-structure.md)  
 <span data-ttu-id="c3a40-120">Uzak makinedeki bir işlemde yüklenen bir CLR örneğini temsil eder.</span><span class="sxs-lookup"><span data-stu-id="c3a40-120">Represents a CLR instance that is loaded in a process on a remote machine.</span></span>  
  
 [<span data-ttu-id="c3a40-121">GetStartupNotificationEvent İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-121">GetStartupNotificationEvent Function</span></span>](getstartupnotificationevent-function.md)  
 <span data-ttu-id="c3a40-122">Belirtilen hedef işlemde yüklenen herhangi bir ortak dil çalışma zamanı (CLR) tarafından işaret edilecek bir olay tanıtıcısı oluşturur veya açar.</span><span class="sxs-lookup"><span data-stu-id="c3a40-122">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
 [<span data-ttu-id="c3a40-123">ICoreClrDebugTarget Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c3a40-123">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)  
 <span data-ttu-id="c3a40-124">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bir bağlantı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="c3a40-124">Creates a connection to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="c3a40-125">InitDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-125">InitDbgTransportManager Function</span></span>](initdbgtransportmanager-function.md)  
 <span data-ttu-id="c3a40-126">İşlem ve çalışma zamanı numaralandırması için uzak hedefe bağlanmak üzere aktarım yöneticisini başlatır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-126">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
 [<span data-ttu-id="c3a40-127">ShutdownDbgTransportManager İşlevi</span><span class="sxs-lookup"><span data-stu-id="c3a40-127">ShutdownDbgTransportManager Function</span></span>](shutdowndbgtransportmanager-function.md)  
 <span data-ttu-id="c3a40-128">Uzak hedef makineye bağlantı için taşıma yöneticisini kapatır.</span><span class="sxs-lookup"><span data-stu-id="c3a40-128">Shuts down the transport manager for a connection to a remote target machine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3a40-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c3a40-129">See also</span></span>

- [<span data-ttu-id="c3a40-130">Hata Ayıklama Coclass’ları</span><span class="sxs-lookup"><span data-stu-id="c3a40-130">Debugging Coclasses</span></span>](debugging-coclasses.md)
- [<span data-ttu-id="c3a40-131">Hata Ayıklama Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="c3a40-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="c3a40-132">Hata Ayıklama Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c3a40-132">Debugging Global Static Functions</span></span>](debugging-global-static-functions.md)
- [<span data-ttu-id="c3a40-133">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="c3a40-133">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="c3a40-134">Hata Ayıklama Yapıları</span><span class="sxs-lookup"><span data-stu-id="c3a40-134">Debugging Structures</span></span>](debugging-structures.md)
