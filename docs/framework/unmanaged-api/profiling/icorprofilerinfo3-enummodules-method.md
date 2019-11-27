---
title: ICorProfilerInfo3::EnumModules Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.EnumModules Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::EnumModules
helpviewer_keywords:
- ICorProfilerInfo3::EnumModules method [.NET Framework profiling]
- EnumModules method [.NET Framework profiling]
ms.assetid: 1bf00b42-69da-4019-91b3-bf88026e83fb
topic_type:
- apiref
ms.openlocfilehash: 0bb2ba56ed93af7861e53d683a0a777107578a6b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449746"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="48a0c-102">ICorProfilerInfo3::EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48a0c-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="48a0c-103">Uygulamaya yüklenen bir yönetilen modüller koleksiyonu aracılığıyla sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="48a0c-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48a0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="48a0c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="48a0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="48a0c-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="48a0c-106">dışı [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="48a0c-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="48a0c-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="48a0c-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48a0c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="48a0c-108">Requirements</span></span>  
 <span data-ttu-id="48a0c-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48a0c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48a0c-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="48a0c-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="48a0c-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="48a0c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48a0c-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48a0c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48a0c-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="48a0c-113">See also</span></span>

- [<span data-ttu-id="48a0c-114">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="48a0c-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="48a0c-115">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="48a0c-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="48a0c-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="48a0c-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="48a0c-117">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="48a0c-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
