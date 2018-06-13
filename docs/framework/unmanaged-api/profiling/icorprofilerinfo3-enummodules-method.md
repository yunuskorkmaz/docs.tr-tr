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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8045e689353a047870c1d93022132846f37dc165
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453704"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="101d7-102">ICorProfilerInfo3::EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="101d7-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="101d7-103">Uygulamaya yüklenen yönetilen modüller koleksiyonu sırayla yinelemek için yöntemler sağlayan bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="101d7-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="101d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="101d7-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="101d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="101d7-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="101d7-106">[out] Bir işaretçi bir [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="101d7-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="101d7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="101d7-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="101d7-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="101d7-108">Requirements</span></span>  
 <span data-ttu-id="101d7-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="101d7-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="101d7-110">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="101d7-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="101d7-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="101d7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="101d7-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="101d7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101d7-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="101d7-113">See Also</span></span>  
 [<span data-ttu-id="101d7-114">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="101d7-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="101d7-115">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="101d7-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="101d7-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="101d7-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="101d7-117">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="101d7-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
