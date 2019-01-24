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
ms.openlocfilehash: 91550d3328acfb5f3bf2ab461fb2d826ee34c580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54545166"
---
# <a name="icorprofilerinfo3enummodules-method"></a><span data-ttu-id="fa27b-102">ICorProfilerInfo3::EnumModules Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa27b-102">ICorProfilerInfo3::EnumModules Method</span></span>
<span data-ttu-id="fa27b-103">Sıralı olarak uygulamasına yüklü yönetilen modülleri koleksiyonu üzerinden yineleme yapmak için yöntemler sağlayan bir numaralandırıcı döndürür.</span><span class="sxs-lookup"><span data-stu-id="fa27b-103">Returns an enumerator that provides methods to sequentially iterate through a collection of managed modules that are loaded into the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa27b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fa27b-104">Syntax</span></span>  
  
```  
HRESULT EnumModules([out] ICorProfilerModuleEnum** ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa27b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fa27b-105">Parameters</span></span>  
 `ppEnum`  
 <span data-ttu-id="fa27b-106">[out] Bir işaretçi bir [Icorprofilermoduleenum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) arabirimi.</span><span class="sxs-lookup"><span data-stu-id="fa27b-106">[out] A pointer to an [ICorProfilerModuleEnum](../../../../docs/framework/unmanaged-api/profiling/icorprofilermoduleenum-interface.md) interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fa27b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fa27b-107">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa27b-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fa27b-108">Requirements</span></span>  
 <span data-ttu-id="fa27b-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa27b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa27b-110">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fa27b-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fa27b-111">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa27b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa27b-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa27b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa27b-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fa27b-113">See also</span></span>
- [<span data-ttu-id="fa27b-114">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fa27b-114">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="fa27b-115">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fa27b-115">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fa27b-116">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fa27b-116">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="fa27b-117">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fa27b-117">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
