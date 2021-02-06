---
description: 'Daha fazla bilgi edinin: ICorProfilerInfo3:: EnumModules yöntemi'
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
ms.openlocfilehash: 9cdb76b77f78fa68eafa111e60b31b738173d658
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646861"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="cfa70-103">ICorProfilerInfo3::EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cfa70-103">ICorProfilerInfo3::EnumModules Method</span></span>

<span data-ttu-id="cfa70-104">Uygulamaya yüklenen bir yönetilen modüller koleksiyonu aracılığıyla sırayla yinelemek için yöntemler sağlayan bir Numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="cfa70-104">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa70-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cfa70-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cfa70-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cfa70-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="cfa70-107">dışı [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) arabirimine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="cfa70-107">[out] A pointer to an [ICorProfilerModuleEnum](icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cfa70-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cfa70-108">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa70-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cfa70-109">Requirements</span></span>  

 <span data-ttu-id="cfa70-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cfa70-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cfa70-111">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cfa70-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cfa70-112">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="cfa70-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cfa70-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cfa70-113">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfa70-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cfa70-114">See also</span></span>

- [<span data-ttu-id="cfa70-115">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa70-115">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="cfa70-116">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cfa70-116">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="cfa70-117">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="cfa70-117">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cfa70-118">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="cfa70-118">Profiling</span></span>](index.md)
