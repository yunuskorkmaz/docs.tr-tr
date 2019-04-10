---
title: ICorProfilerModuleEnum::Clone Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerModuleEnum.Clone Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerModuleEnum::Clone
helpviewer_keywords:
- Clone method, ICorProfilerModuleEnum interface [.NET Framework profiling]
- ICorProfilerModuleEnum::Clone method [.NET Framework profiling]
ms.assetid: 7dec7e36-8d88-416d-b437-abf98b76c1df
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9053505f7356f4618993ead911f730909f53f383
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227151"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="30e0a-102">ICorProfilerModuleEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="30e0a-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="30e0a-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="30e0a-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e0a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="30e0a-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30e0a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="30e0a-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="30e0a-106">[out] Sırayla bu kopyasını işaret eden bir arabirim işaretçisi için bir işaretçi [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="30e0a-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="30e0a-107">Numaralandırıcı kopyasını, bu Numaralandırıcının listesinden kendi sıralaması durumu korur.</span><span class="sxs-lookup"><span data-stu-id="30e0a-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="30e0a-108">Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu aynıdır.</span><span class="sxs-lookup"><span data-stu-id="30e0a-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30e0a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="30e0a-109">Requirements</span></span>  
 <span data-ttu-id="30e0a-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30e0a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30e0a-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="30e0a-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="30e0a-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30e0a-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="30e0a-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="30e0a-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="30e0a-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="30e0a-114">See also</span></span>

- [<span data-ttu-id="30e0a-115">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="30e0a-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="30e0a-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="30e0a-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
