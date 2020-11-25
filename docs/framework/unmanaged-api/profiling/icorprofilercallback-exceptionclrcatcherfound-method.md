---
title: ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionCLRCatcherFound
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type:
- apiref
ms.openlocfilehash: 894084978f976bcee71138d35534a80b5f9cda5f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699982"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="e816c-102">ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e816c-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>

<span data-ttu-id="e816c-103">`catch`Ortak dil çalışma zamanı (CLR) içinde bir özel durum bloğu bulunduğunda çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e816c-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="e816c-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e816c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e816c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e816c-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e816c-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e816c-106">Requirements</span></span>  

 <span data-ttu-id="e816c-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e816c-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e816c-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e816c-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e816c-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e816c-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e816c-110">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="e816c-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e816c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e816c-111">See also</span></span>

- [<span data-ttu-id="e816c-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e816c-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e816c-113">ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e816c-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
