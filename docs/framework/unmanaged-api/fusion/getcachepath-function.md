---
title: GetCachePath İşlevi
ms.date: 03/30/2017
api_name:
- GetCachePath
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- GetCachePath
helpviewer_keywords:
- GetCachePath function [.NET Framework fusion]
ms.assetid: d977ad29-6619-42e1-b0be-bc25ea950e80
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 42bae646b0b1cdd451e01d55ed5b218f3660bb5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33429484"
---
# <a name="getcachepath-function"></a><span data-ttu-id="5a316-102">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="5a316-102">GetCachePath Function</span></span>
<span data-ttu-id="5a316-103">Belirtilen bayraklar kullanarak önbelleğe alınmış derlemeye yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="5a316-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a316-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5a316-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a316-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5a316-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="5a316-106">[in] Bir [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) önbelleğe alınmış derleme kaynağını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="5a316-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="5a316-107">[out] Döndürülen işaretçiyi yolu.</span><span class="sxs-lookup"><span data-stu-id="5a316-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="5a316-108">[içinde out] İstenen en büyük uzunluğu `pwzCachePath`ve return, gerçek uzunluğuyla temel `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="5a316-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a316-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5a316-109">Requirements</span></span>  
 <span data-ttu-id="5a316-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5a316-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a316-111">**Başlık:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="5a316-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="5a316-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a316-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a316-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="5a316-113">See Also</span></span>  
 [<span data-ttu-id="5a316-114">ASM_CACHE_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="5a316-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)  
 [<span data-ttu-id="5a316-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="5a316-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
