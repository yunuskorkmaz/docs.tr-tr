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
ms.openlocfilehash: 9fe35757d895fef3c6267c671f3a91fc50df620a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455686"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="a2cb8-102">ICorProfilerObjectEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2cb8-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="a2cb8-103">Böylece belirtilen sayıda öğeyi atlanır imleci bu Numaralayıcı geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="a2cb8-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2cb8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a2cb8-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2cb8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a2cb8-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a2cb8-106">[in] Atlanan öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="a2cb8-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2cb8-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a2cb8-107">Remarks</span></span>  
 <span data-ttu-id="a2cb8-108">Bu Numaralandırıcının imleç yeni konumu: (geçerli konumu) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="a2cb8-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2cb8-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2cb8-109">Requirements</span></span>  
 <span data-ttu-id="a2cb8-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2cb8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2cb8-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2cb8-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2cb8-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2cb8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2cb8-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2cb8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2cb8-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a2cb8-114">See Also</span></span>  
 [<span data-ttu-id="a2cb8-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2cb8-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
