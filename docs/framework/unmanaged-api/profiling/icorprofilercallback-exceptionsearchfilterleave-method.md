---
title: ICorProfilerCallback::ExceptionSearchFilterLeave Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionSearchFilterLeave
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave
helpviewer_keywords:
- ICorProfilerCallback::ExceptionSearchFilterLeave method [.NET Framework profiling]
- ExceptionSearchFilterLeave method [.NET Framework profiling]
ms.assetid: c28a2a82-dd11-4385-843f-b509fb61753b
topic_type:
- apiref
ms.openlocfilehash: e9679b75e773ec884905ea773e804e03607a61d5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699852"
---
# <a name="icorprofilercallbackexceptionsearchfilterleave-method"></a><span data-ttu-id="a2fbd-102">ICorProfilerCallback::ExceptionSearchFilterLeave Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2fbd-102">ICorProfilerCallback::ExceptionSearchFilterLeave Method</span></span>

<span data-ttu-id="a2fbd-103">Profil oluşturucuyu bir Kullanıcı filtresinin yürütmeyi bitirmekte olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a2fbd-103">Notifies the profiler that a user filter has just finished executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2fbd-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a2fbd-104">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionSearchFilterLeave();  
```  
  
## <a name="requirements"></a><span data-ttu-id="a2fbd-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a2fbd-105">Requirements</span></span>  

 <span data-ttu-id="a2fbd-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2fbd-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2fbd-107">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a2fbd-107">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2fbd-108">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="a2fbd-108">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2fbd-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2fbd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2fbd-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a2fbd-110">See also</span></span>

- [<span data-ttu-id="a2fbd-111">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a2fbd-111">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="a2fbd-112">ExceptionSearchFilterEnter Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a2fbd-112">ExceptionSearchFilterEnter Method</span></span>](icorprofilercallback-exceptionsearchfilterenter-method.md)
