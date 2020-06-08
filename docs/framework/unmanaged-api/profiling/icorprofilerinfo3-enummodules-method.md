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
ms.openlocfilehash: 85adf2dbdbb8c02192a9017bc4f664274a08ee24
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496587"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="0d7a2-102">ICorProfilerInfo3::EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0d7a2-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="0d7a2-103">Uygulamaya yüklenen bir yönetilen modüller koleksiyonu aracılığıyla sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="0d7a2-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d7a2-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="0d7a2-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d7a2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0d7a2-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="0d7a2-106">dışı [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="0d7a2-106">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0d7a2-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0d7a2-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d7a2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0d7a2-108">Requirements</span></span>  
 <span data-ttu-id="0d7a2-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d7a2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d7a2-110">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0d7a2-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0d7a2-111">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="0d7a2-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0d7a2-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d7a2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d7a2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0d7a2-113">See also</span></span>

- [<span data-ttu-id="0d7a2-114">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d7a2-114">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="0d7a2-115">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0d7a2-115">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="0d7a2-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="0d7a2-116">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0d7a2-117">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="0d7a2-117">Profiling</span></span>](index.md)
