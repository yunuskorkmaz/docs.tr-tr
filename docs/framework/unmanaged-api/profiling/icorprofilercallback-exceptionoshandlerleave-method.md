---
description: ': ICorProfilerCallback:: ExceptionOSHandlerLeave yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 809f9440510bc0b55c9cae9827757eb61e61b257
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657583"
---
# <a name="icorprofilercallbackexceptionoshandlerleave-method"></a><span data-ttu-id="ce902-103">ICorProfilerCallback::ExceptionOSHandlerLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce902-103">ICorProfilerCallback::ExceptionOSHandlerLeave Method</span></span>

<span data-ttu-id="ce902-104">Uygulanmaz.</span><span class="sxs-lookup"><span data-stu-id="ce902-104">Not implemented.</span></span> <span data-ttu-id="ce902-105">Yönetilmeyen özel durum bilgisine ihtiyacı olan bir profil oluşturucu, bu bilgileri diğer yollarla almalıdır.</span><span class="sxs-lookup"><span data-stu-id="ce902-105">A profiler that needs unmanaged exception information must obtain this information through other means.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce902-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ce902-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionOSHandlerLeave(  
    [in] UINT_PTR __unused);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ce902-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce902-107">Requirements</span></span>  

 <span data-ttu-id="ce902-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce902-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce902-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ce902-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ce902-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="ce902-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce902-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce902-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce902-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ce902-112">See also</span></span>

- [<span data-ttu-id="ce902-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce902-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
