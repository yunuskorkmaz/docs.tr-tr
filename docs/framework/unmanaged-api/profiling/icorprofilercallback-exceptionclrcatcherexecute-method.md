---
description: ': ICorProfilerCallback:: ExceptionCLRCatcherExecute yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: cb6926fdfcc9b5ffef20cc69c71a3bafefd9f6ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657508"
---
# <a name="icorprofilercallbackexceptionclrcatcherexecute-method"></a><span data-ttu-id="d004a-103">ICorProfilerCallback::ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d004a-103">ICorProfilerCallback::ExceptionCLRCatcherExecute Method</span></span>

<span data-ttu-id="d004a-104">`catch`Ortak dil çalışma zamanı (CLR) içinde bir özel durum bloğu yürütüldüğünde çağırılır.</span><span class="sxs-lookup"><span data-stu-id="d004a-104">Called when a `catch` block for an exception is executed inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="d004a-105">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="d004a-105">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d004a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d004a-106">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherExecute();  
```  
  
## <a name="requirements"></a><span data-ttu-id="d004a-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d004a-107">Requirements</span></span>  

 <span data-ttu-id="d004a-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d004a-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d004a-109">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="d004a-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d004a-110">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="d004a-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d004a-111">**.NET Framework sürümleri:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="d004a-111">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d004a-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d004a-112">See also</span></span>

- [<span data-ttu-id="d004a-113">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d004a-113">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="d004a-114">ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d004a-114">ExceptionCLRCatcherFound Method</span></span>](icorprofilercallback-exceptionclrcatcherfound-method.md)
