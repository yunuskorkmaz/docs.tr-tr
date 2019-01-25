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
ms.openlocfilehash: edbd48c910c89c9dd5feea33d9598933fd63befa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729791"
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="9dd86-102">ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dd86-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="9dd86-103">Çağrılır bir `catch` bir özel durum, ortak dil çalışma zamanı içinde (CLR) kendisi bulunduğunda engelleyin.</span><span class="sxs-lookup"><span data-stu-id="9dd86-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="9dd86-104">Bu yöntem .NET Framework 2.0 sürümünde artık kullanılmıyor.</span><span class="sxs-lookup"><span data-stu-id="9dd86-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9dd86-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9dd86-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="9dd86-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9dd86-106">Requirements</span></span>  
 <span data-ttu-id="9dd86-107">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9dd86-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9dd86-108">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="9dd86-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9dd86-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9dd86-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9dd86-110">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="9dd86-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9dd86-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9dd86-111">See also</span></span>
- [<span data-ttu-id="9dd86-112">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9dd86-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="9dd86-113">ExceptionCLRCatcherExecute Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9dd86-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
