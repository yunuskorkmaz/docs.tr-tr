---
title: ICorProfilerCallback::ExceptionCLRCatcherExecute Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherExecute
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherExecute
helpviewer_keywords:
- ExceptionCLRCatcherExecute method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionCLRCatcherExecute method [.NET Framework profiling]
ms.assetid: aaac8f98-5cf4-42c7-b04b-556cce367e36
topic_type:
- apiref
ms.openlocfilehash: 1a9e377ba98c0c2302e341149bd5acb46c24051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699995"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="3ee8d-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ee8d-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>

<span data-ttu-id="3ee8d-103">`catch`Ortak dil çalışma zamanı (CLR) içinde bir özel durum bloğu yürütüldüğünde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="3ee8d-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="3ee8d-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="3ee8d-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ee8d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3ee8d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3ee8d-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ee8d-106">Requirements</span></span>  

 <span data-ttu-id="3ee8d-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ee8d-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ee8d-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3ee8d-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ee8d-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="3ee8d-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ee8d-110">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="3ee8d-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ee8d-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3ee8d-111">See also</span></span>

- [<span data-ttu-id="3ee8d-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ee8d-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="3ee8d-113">ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ee8d-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
