---
title: "ICorProfilerObjectEnum::Clone Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerObjectEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerObjectEnum interface [.NET Framework profiling]
- ICorProfilerObjectEnum::Clone method [.NET Framework profiling]
ms.assetid: b0b2facd-5991-4f4c-932d-c4937f45cef9
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2d8e478eb9165b4aa5bf019f02f4f128931d928b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerobjectenumclone-method"></a><span data-ttu-id="65a30-102">ICorProfilerObjectEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="65a30-102">ICorProfilerObjectEnum::Clone Method</span></span>
<span data-ttu-id="65a30-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilerobjectenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="65a30-103">Gets an interface pointer to a copy of this [ICorProfilerObjectEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65a30-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="65a30-104">Syntax</span></span>  
  
```  
HRESULT Clone (  
    [out] ICorProfilerObjectEnum   **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="65a30-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="65a30-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="65a30-106">[out] Sırayla bu kopyasını işaret arabirim işaretçisi gösteren bir işaretçi `ICorProfilerObjectEnum` arabirimi.</span><span class="sxs-lookup"><span data-stu-id="65a30-106">[out] A pointer to the interface pointer that in turn points to the copy of this `ICorProfilerObjectEnum` interface.</span></span> <span data-ttu-id="65a30-107">Kopya kendi numaralandırması durumundan ayrı olarak bunu tutar.</span><span class="sxs-lookup"><span data-stu-id="65a30-107">The copy maintains its own enumeration state separately from this one.</span></span> <span data-ttu-id="65a30-108">Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu ile aynı olacaktır.</span><span class="sxs-lookup"><span data-stu-id="65a30-108">However, the copy's initial cursor position will be the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65a30-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="65a30-109">Requirements</span></span>  
 <span data-ttu-id="65a30-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65a30-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65a30-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="65a30-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="65a30-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="65a30-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="65a30-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65a30-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65a30-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="65a30-114">See Also</span></span>  
 [<span data-ttu-id="65a30-115">ICorProfilerObjectEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="65a30-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)
