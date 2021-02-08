---
description: ': ICorProfilerObjectEnum:: Skip yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 8a2aa5dd2b905931b97fafa4db6709aab16aacc4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99781265"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="f954d-103">ICorProfilerObjectEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f954d-103">ICorProfilerObjectEnum::Skip Method</span></span>

<span data-ttu-id="f954d-104">Belirtilen sayıda öğe atlanabilmesi için, bu Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="f954d-104">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f954d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f954d-105">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f954d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f954d-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="f954d-107">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="f954d-107">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f954d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f954d-108">Remarks</span></span>  

 <span data-ttu-id="f954d-109">Bu Numaralandırıcı imlecinizin yeni konumu: (geçerli konum) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="f954d-109">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f954d-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f954d-110">Requirements</span></span>  

 <span data-ttu-id="f954d-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f954d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f954d-112">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f954d-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f954d-113">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="f954d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f954d-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f954d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f954d-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f954d-115">See also</span></span>

- [<span data-ttu-id="f954d-116">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f954d-116">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
