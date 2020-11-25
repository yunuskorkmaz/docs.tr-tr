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
ms.openlocfilehash: c22f0701cfda4523f595366a97435ef8da08b0cb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724474"
---
# <a name="getcachepath-function"></a><span data-ttu-id="187f8-102">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="187f8-102">GetCachePath Function</span></span>

<span data-ttu-id="187f8-103">Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="187f8-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="187f8-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="187f8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="187f8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="187f8-105">Parameters</span></span>  

 `dwCacheFlags`  
 <span data-ttu-id="187f8-106">'ndaki Önbelleğe alınmış derlemenin kaynağını gösteren [asm_cache_flags](asm-cache-flags-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="187f8-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="187f8-107">dışı Yolun döndürülen işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="187f8-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="187f8-108">[in, out] İstenen maksimum uzunluk `pwzCachePath` ve dönüş sonrasında gerçek uzunluğu `pwzCachePath` .</span><span class="sxs-lookup"><span data-stu-id="187f8-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="187f8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="187f8-109">Requirements</span></span>  

 <span data-ttu-id="187f8-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="187f8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="187f8-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="187f8-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="187f8-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="187f8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="187f8-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="187f8-113">See also</span></span>

- [<span data-ttu-id="187f8-114">ASM_CACHE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="187f8-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="187f8-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="187f8-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
