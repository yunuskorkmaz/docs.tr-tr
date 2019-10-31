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
ms.openlocfilehash: 13e1468ef5a48f18910c1f8082cdd7c4849da14a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132694"
---
# <a name="getcachepath-function"></a><span data-ttu-id="d6ea1-102">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="d6ea1-102">GetCachePath Function</span></span>
<span data-ttu-id="d6ea1-103">Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="d6ea1-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ea1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d6ea1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6ea1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d6ea1-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="d6ea1-106">'ndaki Önbelleğe alınmış derlemenin kaynağını gösteren bir [asm_cache_flags](asm-cache-flags-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="d6ea1-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="d6ea1-107">dışı Yolun döndürülen işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="d6ea1-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="d6ea1-108">[in, out] İstenen en büyük `pwzCachePath`uzunluğu ve dönüş sonrasında, `pwzCachePath`gerçek uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="d6ea1-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6ea1-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6ea1-109">Requirements</span></span>  
 <span data-ttu-id="d6ea1-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6ea1-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ea1-111">**Üst bilgi:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="d6ea1-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="d6ea1-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ea1-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ea1-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6ea1-113">See also</span></span>

- [<span data-ttu-id="d6ea1-114">ASM_CACHE_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="d6ea1-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="d6ea1-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="d6ea1-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
