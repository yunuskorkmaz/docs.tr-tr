---
title: "ICorProfilerThreadEnum::Clone Yöntemi"
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
- ICorProfilerThreadEnum.Clone
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Clone method [.NET Framework profiling]
ms.assetid: 5a278bc9-88e2-4c69-b035-9d550dd77081
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d40ef6a9a666f06a46713c6295167cf5e0798ce5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="14a06-102">ICorProfilerThreadEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="14a06-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="14a06-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilerthreadenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="14a06-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14a06-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="14a06-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="14a06-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="14a06-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="14a06-106">[out] Hangi sırayla bu kopyasını işaret arabirim işaretçisi gösteren bir işaretçi [Icorprofilerthreadenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="14a06-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="14a06-107">Kendi numaralandırması durumundan ayrı olarak, bu Numaralandırıcının Numaralandırıcı kopyasını tutar.</span><span class="sxs-lookup"><span data-stu-id="14a06-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="14a06-108">Ancak, kopyanın ilk imleç konumu bu geçerli imleç konumu Numaralayıcı aynıdır.</span><span class="sxs-lookup"><span data-stu-id="14a06-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="14a06-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="14a06-109">Requirements</span></span>  
 <span data-ttu-id="14a06-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="14a06-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="14a06-111">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="14a06-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="14a06-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="14a06-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="14a06-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="14a06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14a06-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="14a06-114">See Also</span></span>  
 [<span data-ttu-id="14a06-115">Icorprofilerthreadenum</span><span class="sxs-lookup"><span data-stu-id="14a06-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)  
 [<span data-ttu-id="14a06-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="14a06-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
