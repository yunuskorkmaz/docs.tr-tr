---
description: 'Şu konuda daha fazla bilgi edinin: ICorProfilerObjectEnum:: Next yöntemi'
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
ms.openlocfilehash: 7f61fa1d4e28043bf5eda95f67dde0d8e87d8c0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781421"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="9d3fd-103">ICorProfilerObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9d3fd-103">ICorProfilerObjectEnum::Next Method</span></span>

<span data-ttu-id="9d3fd-104">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı nesne koleksiyonundan belirtilen sayıda bitişik nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="9d3fd-104">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d3fd-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9d3fd-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9d3fd-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9d3fd-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="9d3fd-107">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="9d3fd-107">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="9d3fd-108">dışı `ObjectID` Her biri alınan bir nesneyi temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="9d3fd-108">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="9d3fd-109">dışı Dizide gerçekten döndürülen öğe sayısına yönelik bir işaretçi `objects` .</span><span class="sxs-lookup"><span data-stu-id="9d3fd-109">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d3fd-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9d3fd-110">Requirements</span></span>  

 <span data-ttu-id="9d3fd-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d3fd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d3fd-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9d3fd-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9d3fd-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="9d3fd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d3fd-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d3fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3fd-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9d3fd-115">See also</span></span>

- [<span data-ttu-id="9d3fd-116">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9d3fd-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
