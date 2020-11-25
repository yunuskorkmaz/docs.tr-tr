---
title: ICorProfilerObjectEnum::Skip Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
ms.openlocfilehash: 83c6af74ebc3eb668317bd64628af17513a2aed6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95702361"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="6c866-102">ICorProfilerObjectEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c866-102">ICorProfilerObjectEnum::Skip Method</span></span>

<span data-ttu-id="6c866-103">Belirtilen sayıda öğe atlanabilmesi için, bu Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="6c866-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c866-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6c866-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c866-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c866-105">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="6c866-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="6c866-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c866-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c866-107">Remarks</span></span>  

 <span data-ttu-id="6c866-108">Bu Numaralandırıcı imlecinizin yeni konumu: (geçerli konum) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="6c866-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c866-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c866-109">Requirements</span></span>  

 <span data-ttu-id="6c866-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c866-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c866-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6c866-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c866-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="6c866-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c866-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c866-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c866-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6c866-114">See also</span></span>

- [<span data-ttu-id="6c866-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c866-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
