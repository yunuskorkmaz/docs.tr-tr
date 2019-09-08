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
ms.openlocfilehash: b1c28f32a4b24393483241bd2d7d6f550b8b65ba
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796899"
---
# <a name="getcachepath-function"></a><span data-ttu-id="c710d-102">GetCachePath İşlevi</span><span class="sxs-lookup"><span data-stu-id="c710d-102">GetCachePath Function</span></span>
<span data-ttu-id="c710d-103">Belirtilen bayrakları kullanarak önbelleğe alınmış derlemenin yolunu alır.</span><span class="sxs-lookup"><span data-stu-id="c710d-103">Gets the path to the cached assembly, using the specified flags.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c710d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c710d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCachePath (  
    [in]      ASM_CACHE_FLAGS  dwCacheFlags,  
    [in]      LPWSTR           pwzCachePath,  
    [in, out] PDWORD           pcchPath  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="c710d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c710d-105">Parameters</span></span>  
 `dwCacheFlags`  
 <span data-ttu-id="c710d-106">'ndaki Önbelleğe alınmış derlemenin kaynağını gösteren bir [asm_cache_flags](asm-cache-flags-enumeration.md) değeri.</span><span class="sxs-lookup"><span data-stu-id="c710d-106">[in] An [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) value that indicates the source of the cached assembly.</span></span>  
  
 `pwzCachePath`  
 <span data-ttu-id="c710d-107">dışı Yolun döndürülen işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c710d-107">[out] The returned pointer to the path.</span></span>  
  
 `pcchPath`  
 <span data-ttu-id="c710d-108">[in, out] İstenen maksimum uzunluk `pwzCachePath`ve dönüş sonrasında gerçek `pwzCachePath`uzunluğu.</span><span class="sxs-lookup"><span data-stu-id="c710d-108">[in, out] The requested maximum length of `pwzCachePath`, and upon return, the actual length of `pwzCachePath`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c710d-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c710d-109">Requirements</span></span>  
 <span data-ttu-id="c710d-110">**Platform** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c710d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c710d-111">**Üst bilgi** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="c710d-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="c710d-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c710d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c710d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c710d-113">See also</span></span>

- [<span data-ttu-id="c710d-114">ASM_CACHE_FLAGS Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="c710d-114">ASM_CACHE_FLAGS Enumeration</span></span>](asm-cache-flags-enumeration.md)
- [<span data-ttu-id="c710d-115">Fusion Genel Statik İşlevleri</span><span class="sxs-lookup"><span data-stu-id="c710d-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
