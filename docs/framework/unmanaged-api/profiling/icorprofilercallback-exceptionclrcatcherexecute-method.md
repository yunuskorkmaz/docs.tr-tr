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
ms.openlocfilehash: b79c8dd9f27805e00535dde53c6ee9f5ee457b42
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500269"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="e56dc-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e56dc-102">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>
<span data-ttu-id="e56dc-103">`catch`Ortak dil çalışma zamanı (CLR) içinde bir özel durum bloğu yürütüldüğünde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e56dc-103">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="e56dc-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e56dc-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e56dc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e56dc-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e56dc-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e56dc-106">Requirements</span></span>  
 <span data-ttu-id="e56dc-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e56dc-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e56dc-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e56dc-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e56dc-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e56dc-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e56dc-110">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="e56dc-110">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e56dc-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e56dc-111">See also</span></span>

- [<span data-ttu-id="e56dc-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e56dc-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e56dc-113">ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e56dc-113">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
