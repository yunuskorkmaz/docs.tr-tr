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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5818cb8d7da7415feb61532799df5fa5a16fd3b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781209"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="c0520-102">ICorProfilerObjectEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0520-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="c0520-103">Belirtilen sayıda öğeyi atlanır, bu Numaralandırıcının imleci geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="c0520-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0520-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0520-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0520-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0520-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="c0520-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="c0520-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0520-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0520-107">Remarks</span></span>  
 <span data-ttu-id="c0520-108">Bu Numaralandırıcının imleç yeni konumu: (geçerli konumu) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="c0520-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0520-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0520-109">Requirements</span></span>  
 <span data-ttu-id="c0520-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0520-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0520-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c0520-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0520-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0520-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0520-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0520-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0520-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0520-114">See also</span></span>

- [<span data-ttu-id="c0520-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0520-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
