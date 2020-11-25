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
ms.openlocfilehash: 6f4fbb40053628d60ba7f094fcb5d50a94d63e1a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729947"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="95c7f-102">RUNTIME_INFO_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="95c7f-102">RUNTIME_INFO_FLAGS Enumeration</span></span>

<span data-ttu-id="95c7f-103">Ortak dil çalışma zamanı (CLR) hakkında hangi bilgilerin döndürüleceğini belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-103">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95c7f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="95c7f-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="95c7f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="95c7f-105">Members</span></span>  
  
|<span data-ttu-id="95c7f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="95c7f-106">Member</span></span>|<span data-ttu-id="95c7f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="95c7f-107">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="95c7f-108">Dizin bilgilerinin içerilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-108">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="95c7f-109">Sürüm bilgisinin dahil edilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-109">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="95c7f-110">Hata sonrasında bir hata iletişim kutusu gösterilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-110">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="95c7f-111">[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevini SEM_FAILCRITICALERRORS bayrağıyla çağırmanın etkilerinin geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-111">Indicates that the effects of calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="95c7f-112">Diğer bir deyişle, bir yükleme iletişim kutusu gizlenmeden önce hata sonrasında gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-112">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="95c7f-113">Çalışma zamanının AMD-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-113">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="95c7f-114">Çalışma zamanının IA-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-114">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="95c7f-115">Çalışma zamanının x86 uyumlu sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-115">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="95c7f-116">Sürüm yükseltme bilgilerinin dahil edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="95c7f-116">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="95c7f-117">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="95c7f-117">Remarks</span></span>  

 <span data-ttu-id="95c7f-118">Aşağıdaki platform mimarisi bayrakları tek seferde belirtilebilir ve birleştirilemez:</span><span class="sxs-lookup"><span data-stu-id="95c7f-118">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="95c7f-119">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="95c7f-119">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="95c7f-120">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="95c7f-120">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="95c7f-121">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="95c7f-121">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95c7f-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="95c7f-122">Requirements</span></span>  

 <span data-ttu-id="95c7f-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95c7f-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95c7f-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="95c7f-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95c7f-125">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="95c7f-125">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95c7f-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95c7f-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c7f-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="95c7f-127">See also</span></span>

- [<span data-ttu-id="95c7f-128">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="95c7f-128">Hosting Enumerations</span></span>](hosting-enumerations.md)
