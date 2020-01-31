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
ms.openlocfilehash: a543e5119a3ad5580fb67c31dc0e59ab62eab571
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866498"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="e9b69-102">ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9b69-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="e9b69-103">Ortak dil çalışma zamanı (CLR) içinde bir özel durum `catch` bloğu bulunduğunda çağırılır.</span><span class="sxs-lookup"><span data-stu-id="e9b69-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="e9b69-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="e9b69-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9b69-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e9b69-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="e9b69-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e9b69-106">Requirements</span></span>  
 <span data-ttu-id="e9b69-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9b69-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9b69-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e9b69-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e9b69-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e9b69-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9b69-110">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="e9b69-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9b69-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e9b69-111">See also</span></span>

- [<span data-ttu-id="e9b69-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e9b69-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e9b69-113">ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e9b69-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
