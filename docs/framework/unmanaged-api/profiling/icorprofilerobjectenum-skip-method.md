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
ms.openlocfilehash: 096489fcdc9d604e003386501c22967b45ba6d7f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861118"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="d4616-102">ICorProfilerObjectEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4616-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="d4616-103">Belirtilen sayıda öğe atlanabilmesi için, bu Numaralandırıcının imlecini geçerli konumundan ilerletir.</span><span class="sxs-lookup"><span data-stu-id="d4616-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4616-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4616-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4616-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d4616-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="d4616-106">'ndaki Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="d4616-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4616-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d4616-107">Remarks</span></span>  
 <span data-ttu-id="d4616-108">Bu Numaralandırıcı imlecinizin yeni konumu: (geçerli konum) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="d4616-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4616-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4616-109">Requirements</span></span>  
 <span data-ttu-id="d4616-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4616-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4616-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d4616-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d4616-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d4616-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4616-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4616-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4616-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4616-114">See also</span></span>

- [<span data-ttu-id="d4616-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4616-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
