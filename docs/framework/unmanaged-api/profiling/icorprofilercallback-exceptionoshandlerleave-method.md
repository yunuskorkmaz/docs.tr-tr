---
title: ICorProfilerCallback::ExceptionOSHandlerLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionOSHandlerLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionOSHandlerLeave
helpviewer_keywords:
- ExceptionOSHandlerLeave method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionOSHandlerLeave method [.NET Framework profiling]
ms.assetid: 4d164676-0ee9-4f67-a8ea-cb474db09053
topic_type:
- apiref
ms.openlocfilehash: e54f87f5f02a1857fd9b7639d00d4bcb976665b1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445410"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="e84bb-102">ICorProfilerCallback::ExceptionOSHandlerLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e84bb-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="e84bb-103">Uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="e84bb-103">Not implemented.</span></span> <span data-ttu-id="e84bb-104">Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.</span><span class="sxs-lookup"><span data-stu-id="e84bb-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e84bb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e84bb-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="e84bb-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e84bb-106">Requirements</span></span>  
 <span data-ttu-id="e84bb-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e84bb-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e84bb-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e84bb-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e84bb-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e84bb-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e84bb-110">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e84bb-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e84bb-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e84bb-111">See also</span></span>

- [<span data-ttu-id="e84bb-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e84bb-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
