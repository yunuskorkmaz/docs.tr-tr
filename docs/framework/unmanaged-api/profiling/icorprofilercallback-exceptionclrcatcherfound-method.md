---
description: ': ICorProfilerCallback:: ExceptionCLRCatcherFound yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 37027a00e488eed5681b1d99ada6332d59e6a632
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706311"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="1ed1c-103">ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ed1c-103">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>

<span data-ttu-id="1ed1c-104">`catch`Ortak dil çalışma zamanı (CLR) içinde bir özel durum bloğu bulunduğunda çağırılır.</span><span class="sxs-lookup"><span data-stu-id="1ed1c-104">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="1ed1c-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="1ed1c-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ed1c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="1ed1c-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="1ed1c-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1ed1c-107">Requirements</span></span>  

 <span data-ttu-id="1ed1c-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ed1c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1ed1c-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1ed1c-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1ed1c-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1ed1c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1ed1c-111">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="1ed1c-111">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ed1c-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1ed1c-112">See also</span></span>

- [<span data-ttu-id="1ed1c-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1ed1c-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1ed1c-114">ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1ed1c-114">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
