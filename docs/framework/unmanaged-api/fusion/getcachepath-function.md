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
ms.openlocfilehash: 92366190c769344b41923cbb25ed4b04afceaae9
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778661"
---
# <a name="getcachepath-function"></a><span data-ttu-id="05fd8-102">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="05fd8-102">GetCachePath Function</span></span>
<span data-ttu-id="05fd8-103">Belirtilen bayraklar kullanarak önbelleğe alınmış derleme yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="05fd8-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05fd8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="05fd8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="05fd8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="05fd8-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="05fd8-106">[in] Bir [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) önbelleğe alınan bir derleme kaynağını belirten değer.</span><span class="sxs-lookup"><span data-stu-id="05fd8-106">[in] An [ASM_CACHE_FLAGS](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="05fd8-107">[out] Döndürülen işaretçi yolu.</span><span class="sxs-lookup"><span data-stu-id="05fd8-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="05fd8-108">[out içinde] İstenen maksimum uzunluğunu `pwzCachePath`ve iade, gerçek uzunluğunu temel `pwzCachePath`.</span><span class="sxs-lookup"><span data-stu-id="05fd8-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05fd8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="05fd8-109">Requirements</span></span>  
 <span data-ttu-id="05fd8-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05fd8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05fd8-111">**Üst bilgi:** Fusion.h</span><span class="sxs-lookup"><span data-stu-id="05fd8-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="05fd8-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05fd8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05fd8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="05fd8-113">See also</span></span>

- [<span data-ttu-id="05fd8-114">ASM_CACHE_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="05fd8-114">ASM_CACHE_FLAGS Enumeration</span></span>](../../../../docs/framework/unmanaged-api/fusion/asm-cache-flags-enumeration.md)
- [<span data-ttu-id="05fd8-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="05fd8-115">Fusion Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-global-static-functions.md)
