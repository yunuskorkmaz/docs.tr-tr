---
title: ICorProfilerThreadEnum::Clone Yöntemi
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0301334621a2e393a59e7cc34f2964450a81213f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61597053"
---
# <a name="icorprofilerthreadenumclone-method"></a><span data-ttu-id="25568-102">ICorProfilerThreadEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="25568-102">ICorProfilerThreadEnum::Clone Method</span></span>
<span data-ttu-id="25568-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilerthreadenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="25568-103">Gets an interface pointer to a copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25568-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="25568-104">Syntax</span></span>  
  
```  
HRESULT Clone (    [out] ICorProfilerThreadEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25568-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="25568-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="25568-106">[out] Sırayla bu kopyasını işaret eden bir arabirim işaretçisi için bir işaretçi [Icorprofilerthreadenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="25568-106">[out] A pointer to the interface pointer, which, in turn, points to the copy of this [ICorProfilerThreadEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md) interface.</span></span> <span data-ttu-id="25568-107">Numaralandırıcı kopyasını, bu Numaralandırıcının listesinden kendi sıralaması durumu korur.</span><span class="sxs-lookup"><span data-stu-id="25568-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="25568-108">Ancak, kopyanın ilk imleç konumu numaralandırıcıyı Bu geçerli imleç konumundan aynıdır.</span><span class="sxs-lookup"><span data-stu-id="25568-108">However, the initial cursor position of the copy is the same as this current cursor position of the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25568-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="25568-109">Requirements</span></span>  
 <span data-ttu-id="25568-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25568-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25568-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="25568-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="25568-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="25568-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25568-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25568-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25568-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="25568-114">See also</span></span>

- [<span data-ttu-id="25568-115">Icorprofilerthreadenum</span><span class="sxs-lookup"><span data-stu-id="25568-115">ICorProfilerThreadEnum</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="25568-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="25568-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
