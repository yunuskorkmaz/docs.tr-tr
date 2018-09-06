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
ms.openlocfilehash: 09bd32172bcad298eebc2921461fdc953e9c6d6e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43866166"
---
# <a name="runtimeinfoflags-enumeration"></a><span data-ttu-id="54c71-102">RUNTIME_INFO_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="54c71-102">RUNTIME_INFO_FLAGS Enumeration</span></span>
<span data-ttu-id="54c71-103">Ortak dil çalışma zamanı (CLR) hakkında bilgiler döndürülmesi gerektiğini gösteren değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="54c71-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c71-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="54c71-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="54c71-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="54c71-105">Members</span></span>  
  
|<span data-ttu-id="54c71-106">Üye</span><span class="sxs-lookup"><span data-stu-id="54c71-106">Member</span></span>|<span data-ttu-id="54c71-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="54c71-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="54c71-108">Dizin bilgileri eklenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54c71-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="54c71-109">Sürüm bilgileri eklenmeyeceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54c71-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="54c71-110">Bir hata iletişim kutusu başarısızlık durumunda gösterilecek değil olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="54c71-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="54c71-111">Bildiren arama etkilerini [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) SEM_FAILCRITICALERRORS bayrağıyla işlevi geçersiz.</span><span class="sxs-lookup"><span data-stu-id="54c71-111">Indicates that the effects of calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="54c71-112">Diğer bir deyişle, bir yükleme iletişim kutusu yok yerine başarısızlık gösterilmesi gerekir.</span><span class="sxs-lookup"><span data-stu-id="54c71-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="54c71-113">Bir çalışma zamanı AMD 64 uyumlu sürümü hakkında daha fazla bilgi için bir istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="54c71-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="54c71-114">Bir çalışma zamanı IA-64-compatible sürümü hakkında daha fazla bilgi için bir istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="54c71-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="54c71-115">Bir çalışma zamanı x86 uyumlu sürümü hakkında daha fazla bilgi için bir istek gösterir.</span><span class="sxs-lookup"><span data-stu-id="54c71-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="54c71-116">Sürüm yükseltme bilgileri dahil olması gerektiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="54c71-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54c71-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="54c71-117">Remarks</span></span>  
 <span data-ttu-id="54c71-118">Aşağıdaki platform mimarisi bayrakları belirtilen tek bir zaman olabilir ve birleştirilemez:</span><span class="sxs-lookup"><span data-stu-id="54c71-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
-   <span data-ttu-id="54c71-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="54c71-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
-   <span data-ttu-id="54c71-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="54c71-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
-   <span data-ttu-id="54c71-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="54c71-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54c71-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="54c71-122">Requirements</span></span>  
 <span data-ttu-id="54c71-123">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54c71-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54c71-124">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54c71-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54c71-125">**Kitaplığı:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54c71-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54c71-126">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54c71-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54c71-127">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="54c71-127">See Also</span></span>  
 [<span data-ttu-id="54c71-128">Barındırma Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="54c71-128">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
