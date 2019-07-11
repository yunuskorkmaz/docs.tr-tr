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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 468c5b28bb5a574aacf623196f0c516992473707
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67756233"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="07d3e-102">ICorProfilerCallback::ExceptionOSHandlerLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07d3e-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="07d3e-103">Henüz uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="07d3e-103">Not implemented.</span></span> <span data-ttu-id="07d3e-104">Yönetilmeyen özel durum bilgisi gerektiren bir profil oluşturucu, diğer araçlarla bu bilgileri edinmeniz gerekir.</span><span class="sxs-lookup"><span data-stu-id="07d3e-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07d3e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="07d3e-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="07d3e-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07d3e-106">Requirements</span></span>  
 <span data-ttu-id="07d3e-107">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07d3e-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07d3e-108">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07d3e-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07d3e-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07d3e-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07d3e-110">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07d3e-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07d3e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07d3e-111">See also</span></span>

- [<span data-ttu-id="07d3e-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07d3e-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
