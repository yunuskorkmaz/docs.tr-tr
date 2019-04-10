---
title: RUNTIME_INFO_FLAGS Numaralandırması
ms.date: 03/30/2017
api_name:
- RUNTIME_INFO_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RUNTIME_INFO_FLAGS
helpviewer_keywords:
- RUNTIME_INFO_FLAGS enumeration [.NET Framework hosting]
ms.assetid: adba37be-f775-4cdb-8919-5746ce694f33
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9483cf8671b7d3ad5430081d93925af30b3d8368
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215696"
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="bb53e-102">RUNTIME_INFO_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="bb53e-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="bb53e-103">Ortak dil çalışma zamanı (CLR) hakkında bilgiler döndürülmesi gerektiğini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb53e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bb53e-104">Syntax</span></span>  
  
```  
typedef enum {  
  
    RUNTIME_INFO_UPGRADE_VERSION             = 0x01,  
    RUNTIME_INFO_REQUEST_IA64                = 0x02,  
    RUNTIME_INFO_REQUEST_AMD64               = 0x04,  
    RUNTIME_INFO_REQUEST_X86                 = 0x08,  
    RUNTIME_INFO_DONT_RETURN_DIRECTORY       = 0x10,  
    RUNTIME_INFO_DONT_RETURN_VERSION         = 0x20,  
    RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG      = 0x40,  
    RUNTIME_INFO_IGNORE_ERROR_MODE           = 0x1000  
  
} RUNTIME_INFO_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="bb53e-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="bb53e-105">Members</span></span>  
  
|<span data-ttu-id="bb53e-106">Üye</span><span class="sxs-lookup"><span data-stu-id="bb53e-106">Member</span></span>|<span data-ttu-id="bb53e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bb53e-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="bb53e-108">Dizin bilgileri eklenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="bb53e-109">Sürüm bilgileri eklenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="bb53e-110">Bir hata iletişim kutusu başarısızlık durumunda gösterilecek değil olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="bb53e-111">Bildiren arama etkilerini [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS bayrağıyla işlevi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="bb53e-111">Indicates that the effects of calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="bb53e-112">Diğer bir deyişle, bir yükleme iletişim kutusu yok yerine başarısızlık gösterilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="bb53e-113">Bir çalışma zamanı AMD 64 uyumlu sürümü hakkında daha fazla bilgi için bir istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="bb53e-114">Bir çalışma zamanı IA-64-compatible sürümü hakkında daha fazla bilgi için bir istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="bb53e-115">Bir çalışma zamanı x86 uyumlu sürümü hakkında daha fazla bilgi için bir istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="bb53e-116">Sürüm yükseltme bilgileri dahil olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="bb53e-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb53e-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bb53e-117">Remarks</span></span>  
 <span data-ttu-id="bb53e-118">Aşağıdaki platform mimarisi bayrakları belirtilen tek bir zaman olabilir ve birleştirilemez:</span><span class="sxs-lookup"><span data-stu-id="bb53e-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="bb53e-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="bb53e-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="bb53e-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="bb53e-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="bb53e-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="bb53e-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb53e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bb53e-122">Requirements</span></span>  
 <span data-ttu-id="bb53e-123">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb53e-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb53e-124">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="bb53e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb53e-125">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb53e-125">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="bb53e-126">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="bb53e-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bb53e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bb53e-127">See also</span></span>

- [<span data-ttu-id="bb53e-128">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="bb53e-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
