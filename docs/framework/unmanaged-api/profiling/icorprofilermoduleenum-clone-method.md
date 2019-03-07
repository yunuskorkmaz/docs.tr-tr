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
ms.openlocfilehash: fd3e3739ea9b5330f456156c0455009d90478649
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57470477"
---
# <a name="icorprofilermoduleenumclone-method"></a><span data-ttu-id="ea672-102">ICorProfilerModuleEnum::Clone Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ea672-102">ICorProfilerModuleEnum::Clone Method</span></span>
<span data-ttu-id="ea672-103">Bu bir kopyasını bir arabirim işaretçisi alır [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ea672-103">Gets an interface pointer to a copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea672-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ea672-104">Syntax</span></span>  
  
```  
HRESULT Clone([out] ICorProfilerObjectEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ea672-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ea672-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="ea672-106">[out] Sırayla bu kopyasını işaret eden bir arabirim işaretçisi için bir işaretçi [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="ea672-106">[out] A pointer to the interface pointer that in turn points to the copy of this [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span> <span data-ttu-id="ea672-107">Numaralandırıcı kopyasını, bu Numaralandırıcının listesinden kendi sıralaması durumu korur.</span><span class="sxs-lookup"><span data-stu-id="ea672-107">The copy of the enumerator maintains its own enumeration state separately from this enumerator.</span></span> <span data-ttu-id="ea672-108">Ancak, kopyanın ilk imleç konumu bu Numaralandırıcının geçerli imleç konumu aynıdır.</span><span class="sxs-lookup"><span data-stu-id="ea672-108">However, the copy's initial cursor position is the same as this enumerator's current cursor position.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ea672-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ea672-109">Requirements</span></span>  
 <span data-ttu-id="ea672-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea672-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea672-111">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ea672-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ea672-112">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ea672-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ea672-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea672-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea672-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ea672-114">See also</span></span>
- [<span data-ttu-id="ea672-115">ICorProfilerModuleEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ea672-115">ICorProfilerModuleEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md)
- [<span data-ttu-id="ea672-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="ea672-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
