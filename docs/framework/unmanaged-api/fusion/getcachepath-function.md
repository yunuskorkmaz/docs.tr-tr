---
description: 'Daha fazla bilgi edinin: GetCachePath Işlevi'
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
ms.openlocfilehash: 4f5045d4110ca9aae33ef54eb85a2146f855e6c7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761050"
---
# <a name="getcachepath-function"></a><span data-ttu-id="418e2-103">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="418e2-103">GetCachePath Function</span></span>

<span data-ttu-id="418e2-104">Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="418e2-104">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="418e2-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="418e2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="418e2-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="418e2-106">Parameters</span></span>  

 `dwCacheFlags`  
 <span data-ttu-id="418e2-107">'ndaki Önbelleğe alınmış derlemenin kaynağını gösteren [asm_cache_flags](asm-cache-flags-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="418e2-107">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="418e2-108">dışı Yolun döndürülen işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="418e2-108">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="418e2-109">[in, out] İstenen maksimum uzunluk `pwzCachePath` ve dönüş sonrasında gerçek uzunluğu `pwzCachePath` .</span><span class="sxs-lookup"><span data-stu-id="418e2-109">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="418e2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="418e2-110">Requirements</span></span>  

 <span data-ttu-id="418e2-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="418e2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="418e2-112">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="418e2-112">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="418e2-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="418e2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="418e2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="418e2-114">See also</span></span>

- [<span data-ttu-id="418e2-115">ASM_CACHE_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="418e2-115">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="418e2-116">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="418e2-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
