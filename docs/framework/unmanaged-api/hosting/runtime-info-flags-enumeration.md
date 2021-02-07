---
description: 'Hakkında daha fazla bilgi edinin: RUNTIME_INFO_FLAGS numaralandırması'
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
ms.openlocfilehash: 54ff62cdee6e940ae9ea8a2ce8ceff99f923d3f4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679452"
---
# <a name="runtime_info_flags-enumeration"></a><span data-ttu-id="7607c-103">RUNTIME_INFO_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7607c-103">RUNTIME_INFO_FLAGS Enumeration</span></span>

<span data-ttu-id="7607c-104">Ortak dil çalışma zamanı (CLR) hakkında hangi bilgilerin döndürüleceğini belirten değerleri içerir.</span><span class="sxs-lookup"><span data-stu-id="7607c-104">Contains values that indicate what information about the common language runtime (CLR) should be returned.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7607c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7607c-105">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="7607c-106">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7607c-106">Members</span></span>  
  
|<span data-ttu-id="7607c-107">Üye</span><span class="sxs-lookup"><span data-stu-id="7607c-107">Member</span></span>|<span data-ttu-id="7607c-108">Description</span><span class="sxs-lookup"><span data-stu-id="7607c-108">Description</span></span>|  
|------------|-----------------|  
|`RUNTIME_INFO_DONT_RETURN_DIRECTORY`|<span data-ttu-id="7607c-109">Dizin bilgilerinin içerilmeyeceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7607c-109">Indicates that directory information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_RETURN_VERSION`|<span data-ttu-id="7607c-110">Sürüm bilgisinin dahil edilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7607c-110">Indicates that version information should not be included.</span></span>|  
|`RUNTIME_INFO_DONT_SHOW_ERROR_DIALOG`|<span data-ttu-id="7607c-111">Hata sonrasında bir hata iletişim kutusu gösterilmemelidir.</span><span class="sxs-lookup"><span data-stu-id="7607c-111">Indicates that an error dialog box should not be shown upon failure.</span></span>|  
|`RUNTIME_INFO_IGNORE_ERROR_MODE`|<span data-ttu-id="7607c-112">[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) işlevini SEM_FAILCRITICALERRORS bayrağıyla çağırmanın etkilerinin geçersiz kılınabileceğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="7607c-112">Indicates that the effects of calling the [SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) function with the SEM_FAILCRITICALERRORS flag should be overridden.</span></span> <span data-ttu-id="7607c-113">Diğer bir deyişle, bir yükleme iletişim kutusu gizlenmeden önce hata sonrasında gösterilmelidir.</span><span class="sxs-lookup"><span data-stu-id="7607c-113">That is, an installation dialog box should be shown upon failure, instead of being suppressed.</span></span>|  
|`RUNTIME_INFO_REQUEST_AMD64`|<span data-ttu-id="7607c-114">Çalışma zamanının AMD-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="7607c-114">Indicates a request for information about an AMD-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_IA64`|<span data-ttu-id="7607c-115">Çalışma zamanının IA-64 ile uyumlu bir sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="7607c-115">Indicates a request for information about an IA-64-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_REQUEST_X86`|<span data-ttu-id="7607c-116">Çalışma zamanının x86 uyumlu sürümü hakkında bilgi isteği gösterir.</span><span class="sxs-lookup"><span data-stu-id="7607c-116">Indicates a request for information about an x86-compatible version of the runtime.</span></span>|  
|`RUNTIME_INFO_UPGRADE_VERSION`|<span data-ttu-id="7607c-117">Sürüm yükseltme bilgilerinin dahil edileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="7607c-117">Indicates that version upgrade information should be included.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7607c-118">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7607c-118">Remarks</span></span>  

 <span data-ttu-id="7607c-119">Aşağıdaki platform mimarisi bayrakları tek seferde belirtilebilir ve birleştirilemez:</span><span class="sxs-lookup"><span data-stu-id="7607c-119">The following platform architecture flags can be specified only one at a time and cannot be combined:</span></span>  
  
- <span data-ttu-id="7607c-120">RUNTIME_INFO_REQUEST_IA64</span><span class="sxs-lookup"><span data-stu-id="7607c-120">RUNTIME_INFO_REQUEST_IA64</span></span>  
  
- <span data-ttu-id="7607c-121">RUNTIME_INFO_REQUEST_AMD64</span><span class="sxs-lookup"><span data-stu-id="7607c-121">RUNTIME_INFO_REQUEST_AMD64</span></span>  
  
- <span data-ttu-id="7607c-122">RUNTIME_INFO_REQUEST_X86</span><span class="sxs-lookup"><span data-stu-id="7607c-122">RUNTIME_INFO_REQUEST_X86</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7607c-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7607c-123">Requirements</span></span>  

 <span data-ttu-id="7607c-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7607c-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7607c-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7607c-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7607c-126">**Kitaplık:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7607c-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7607c-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7607c-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7607c-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7607c-128">See also</span></span>

- [<span data-ttu-id="7607c-129">Barındırma Numaralandırmaları</span><span class="sxs-lookup"><span data-stu-id="7607c-129">Hosting Enumerations</span></span>](hosting-enumerations.md)
