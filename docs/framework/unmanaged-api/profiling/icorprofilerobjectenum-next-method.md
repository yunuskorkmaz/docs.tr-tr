---
title: ICorProfilerObjectEnum::Next Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Next
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Next
helpviewer_keywords:
- Next method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Next method [.NET Framework profiling]
ms.assetid: b420433c-5ebe-4986-bba1-97902e6db819
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8c938c7c51c867d8e8d8d23390a3c16a23084fbc
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775013"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="6aebf-102">ICorProfilerObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6aebf-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="6aebf-103">Belirtilen bitişik nesne sayısı dizideki geçerli konum Numaralandırıcının başlayarak nesnelerin sıralı bir koleksiyonu alır.</span><span class="sxs-lookup"><span data-stu-id="6aebf-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aebf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6aebf-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]    
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aebf-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6aebf-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6aebf-106">[in] Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="6aebf-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="6aebf-107">[out] Bir dizi `ObjectID` değerler, her biri alınan bir nesneyi temsil eder.</span><span class="sxs-lookup"><span data-stu-id="6aebf-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6aebf-108">[out] Gerçekte döndürülen öğe sayısına bir işaretçi `objects` dizisi.</span><span class="sxs-lookup"><span data-stu-id="6aebf-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aebf-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6aebf-109">Requirements</span></span>  
 <span data-ttu-id="6aebf-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6aebf-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aebf-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6aebf-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6aebf-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aebf-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aebf-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aebf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aebf-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6aebf-114">See also</span></span>

- [<span data-ttu-id="6aebf-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6aebf-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
