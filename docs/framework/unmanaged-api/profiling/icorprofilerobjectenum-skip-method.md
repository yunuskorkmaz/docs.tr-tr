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
ms.openlocfilehash: 3c573c709e765fa723a726f5c8990ba59222ed1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428131"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="cf9fe-102">ICorProfilerObjectEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf9fe-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="cf9fe-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span><span class="sxs-lookup"><span data-stu-id="cf9fe-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf9fe-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf9fe-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf9fe-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cf9fe-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="cf9fe-106">[in] The number of elements to be skipped.</span><span class="sxs-lookup"><span data-stu-id="cf9fe-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cf9fe-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf9fe-107">Remarks</span></span>  
 <span data-ttu-id="cf9fe-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="cf9fe-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf9fe-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf9fe-109">Requirements</span></span>  
 <span data-ttu-id="cf9fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf9fe-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf9fe-111">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cf9fe-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cf9fe-112">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cf9fe-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cf9fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cf9fe-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf9fe-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf9fe-114">See also</span></span>

- [<span data-ttu-id="cf9fe-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf9fe-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
