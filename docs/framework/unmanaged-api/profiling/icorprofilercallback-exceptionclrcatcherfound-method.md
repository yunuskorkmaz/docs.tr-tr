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
ms.openlocfilehash: 4f4d53b086453adce38902518f2de3dde1f2812f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500253"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="8c18f-102">ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c18f-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="8c18f-103">`catch`Ortak dil çalışma zamanı (CLR) içinde bir özel durum bloğu bulunduğunda çağırılır.</span><span class="sxs-lookup"><span data-stu-id="8c18f-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="8c18f-104">Bu yöntem .NET Framework sürüm 2,0 ' de kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="8c18f-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c18f-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c18f-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="8c18f-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c18f-106">Requirements</span></span>  
 <span data-ttu-id="8c18f-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c18f-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c18f-108">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8c18f-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8c18f-109">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8c18f-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8c18f-110">**.NET Framework sürümü:** 1,0</span><span class="sxs-lookup"><span data-stu-id="8c18f-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c18f-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c18f-111">See also</span></span>

- [<span data-ttu-id="8c18f-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c18f-112">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8c18f-113">ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c18f-113">ExceptionCLRCatcherExecute Method</span></span>](icorprofilercallback-exceptionclrcatcherexecute-method.md)
