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
ms.openlocfilehash: 850f05520e4146b5016bb574f02aa800dfcaaf32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494585"
---
# <a name="icorprofilerobjectenumnext-method"></a><span data-ttu-id="0704a-102">ICorProfilerObjectEnum::Next Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0704a-102">ICorProfilerObjectEnum::Next Method</span></span>
<span data-ttu-id="0704a-103">Numaralandırıcının dizideki geçerli konumundan başlayarak sıralı nesne koleksiyonundan belirtilen sayıda bitişik nesneyi alır.</span><span class="sxs-lookup"><span data-stu-id="0704a-103">Gets the specified number of contiguous objects from a sequential collection of objects, starting at the enumerator's current position in the sequence.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0704a-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0704a-104">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG                    celt,  
    [out, size_is(celt), length_is(*pceltFetched)]
        ObjectID                  objects[],  
    [out] ULONG                   *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0704a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0704a-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0704a-106">'ndaki Alınacak nesne sayısı.</span><span class="sxs-lookup"><span data-stu-id="0704a-106">[in] The number of objects to be retrieved.</span></span>  
  
 `objects`  
 <span data-ttu-id="0704a-107">dışı `ObjectID`Her biri alınan bir nesneyi temsil eden bir değer dizisi.</span><span class="sxs-lookup"><span data-stu-id="0704a-107">[out] An array of `ObjectID` values, each of which represents a retrieved object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="0704a-108">dışı Dizide gerçekten döndürülen öğe sayısına yönelik bir işaretçi `objects` .</span><span class="sxs-lookup"><span data-stu-id="0704a-108">[out] A pointer to the number of elements actually returned in the `objects` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0704a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0704a-109">Requirements</span></span>  
 <span data-ttu-id="0704a-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0704a-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0704a-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0704a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0704a-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0704a-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0704a-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0704a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0704a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0704a-114">See also</span></span>

- [<span data-ttu-id="0704a-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0704a-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
