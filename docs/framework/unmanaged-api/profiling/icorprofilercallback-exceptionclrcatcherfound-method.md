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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 683cec06cd4c2fdef310126adc2921c858ca5687
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776033"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="af83b-102">ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af83b-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="af83b-103">Çağrılır bir `catch` bir özel durum, ortak dil çalışma zamanı içinde (CLR) kendisi bulunduğunda engelleyin.</span><span class="sxs-lookup"><span data-stu-id="af83b-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="af83b-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="af83b-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af83b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="af83b-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="af83b-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af83b-106">Requirements</span></span>  
 <span data-ttu-id="af83b-107">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af83b-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af83b-108">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="af83b-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="af83b-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="af83b-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="af83b-110">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="af83b-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af83b-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af83b-111">See also</span></span>

- [<span data-ttu-id="af83b-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af83b-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="af83b-113">ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af83b-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
