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
ms.openlocfilehash: 5ba45cf526a6ebca6975a75d06308d089770ad5b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500279"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="b779e-102">ICorProfilerCallback::ExceptionOSHandlerLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b779e-102">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>
<span data-ttu-id="b779e-103">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="b779e-103">Not implemented.</span></span> <span data-ttu-id="b779e-104">Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.</span><span class="sxs-lookup"><span data-stu-id="b779e-104">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b779e-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b779e-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b779e-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b779e-106">Requirements</span></span>  
 <span data-ttu-id="b779e-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b779e-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b779e-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b779e-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b779e-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b779e-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b779e-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b779e-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b779e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b779e-111">See also</span></span>

- [<span data-ttu-id="b779e-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b779e-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
