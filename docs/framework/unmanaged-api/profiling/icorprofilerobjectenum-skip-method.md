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
ms.openlocfilehash: 2bcc837fede7e7db59bdf88a0b5434a7c1924335
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597118"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="ff734-102">ICorProfilerObjectEnum::Skip Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ff734-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="ff734-103">Belirtilen sayıda öğeyi atlanır, bu Numaralandırıcının imleci geçerli konumundan ilerler.</span><span class="sxs-lookup"><span data-stu-id="ff734-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff734-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ff734-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff734-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ff734-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ff734-106">[in] Atlanacak öğe sayısı.</span><span class="sxs-lookup"><span data-stu-id="ff734-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff734-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ff734-107">Remarks</span></span>  
 <span data-ttu-id="ff734-108">Bu Numaralandırıcının imleç yeni konumu: (geçerli konumu) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="ff734-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff734-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ff734-109">Requirements</span></span>  
 <span data-ttu-id="ff734-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff734-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff734-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff734-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff734-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff734-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff734-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff734-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff734-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ff734-114">See also</span></span>

- [<span data-ttu-id="ff734-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ff734-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
