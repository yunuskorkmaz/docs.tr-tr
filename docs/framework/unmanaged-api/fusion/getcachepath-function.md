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
ms.openlocfilehash: cf23a8f1893aa0f992d554d3c7533c3dc42f4e95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150988"
---
# <a name="getcachepath-function"></a><span data-ttu-id="9d80e-102">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="9d80e-102">GetCachePath Function</span></span>
<span data-ttu-id="9d80e-103">Belirtilen bayraklar kullanarak önbelleğe alınmış derleme yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="9d80e-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d80e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d80e-104">Syntax</span></span>  
  
```  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d80e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d80e-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="9d80e-106">[in] Bir [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) önbelleğe alınan bir derleme kaynağını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="9d80e-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="9d80e-107">[out] Döndürülen işaretçi yolu.</span><span class="sxs-lookup"><span data-stu-id="9d80e-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="9d80e-108">[out içinde] İstenen maksimum uzunluğunu `pwzCachePath`ve iade, gerçek uzunluğunu temel `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="9d80e-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d80e-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d80e-109">Requirements</span></span>  
 <span data-ttu-id="9d80e-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d80e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d80e-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="9d80e-111">**Header:** Fusion.h</span></span>  
  
 **<span data-ttu-id="9d80e-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9d80e-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9d80e-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d80e-113">See also</span></span>

- [<span data-ttu-id="9d80e-114">ASM_CACHE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="9d80e-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [<span data-ttu-id="9d80e-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="9d80e-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
