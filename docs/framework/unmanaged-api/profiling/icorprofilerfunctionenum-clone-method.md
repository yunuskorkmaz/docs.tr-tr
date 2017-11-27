---
title: "ICorProfilerFunctionEnum::Clone Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerFunctionEnum.Clone Method
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerFunctionEnum::Clone
helpviewer_keywords:
- ICorProfilerFunctionEnum::Clone method [.NET Framework profiling]
- Clone method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
ms.assetid: 0c3d4835-e111-4e82-af6d-53f140b8f2c9
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: dc1d14a1480c3634993190448f9beff911bebf6d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerfunctionenumclone-method"></a><span data-ttu-id="64eda-102">ICorProfilerFunctionEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="64eda-102">ICorProfilerFunctionEnum::Clone Method</span></span>
<span data-ttu-id="64eda-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="64eda-103">Gets an interface pointer to a copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64eda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="64eda-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerFunctionEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64eda-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="64eda-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="64eda-106">[out] Hangi sırayla bu kopyasını işaret arabirim işaretçisi gösteren bir işaretçi [Icorprofilerfunctionenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="64eda-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerFunctionEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md) interface.</span></span> <span data-ttu-id="64eda-107">Kendi numaralandırması durumundan ayrı olarak, bu Numaralandırıcının Numaralandırıcı kopyasını tutar.</span><span class="sxs-lookup"><span data-stu-id="64eda-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="64eda-108">Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu aynıdır.</span><span class="sxs-lookup"><span data-stu-id="64eda-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64eda-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="64eda-109">Requirements</span></span>  
 <span data-ttu-id="64eda-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64eda-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64eda-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64eda-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64eda-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64eda-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64eda-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="64eda-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64eda-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="64eda-114">See Also</span></span>  
 [<span data-ttu-id="64eda-115">Icorprofilerfunctionenum arabirimi</span><span class="sxs-lookup"><span data-stu-id="64eda-115">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="64eda-116">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="64eda-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
