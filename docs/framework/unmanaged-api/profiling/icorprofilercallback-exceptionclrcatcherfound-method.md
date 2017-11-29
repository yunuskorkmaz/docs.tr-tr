---
title: "ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ExceptionCLRCatcherFound
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ExceptionCLRCatcherFound
helpviewer_keywords:
- ICorProfilerCallback::ExceptionCLRCatcherFound method [.NET Framework profiling]
- ExceptionCLRCatcherFound method [.NET Framework profiling]
ms.assetid: 73fe8b4b-8f9a-4ba5-a10c-b26521396a66
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebb1779ca9f09089a071673f92810ea7a9e76b3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackexceptionclrcatcherfound-method"></a><span data-ttu-id="2f32d-102">ICorProfilerCallback::ExceptionCLRCatcherFound Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f32d-102">ICorProfilerCallback::ExceptionCLRCatcherFound Method</span></span>
<span data-ttu-id="2f32d-103">Ne zaman adlı bir `catch` bir özel durum ortak dil çalışma zamanı içinde (CLR) kendisi bulunduğunda engelleyin.</span><span class="sxs-lookup"><span data-stu-id="2f32d-103">Called when a `catch` block for an exception is found inside the common language runtime (CLR) itself.</span></span> <span data-ttu-id="2f32d-104">Bu yöntem .NET Framework 2.0 sürümünde kullanımdan kalkmıştır.</span><span class="sxs-lookup"><span data-stu-id="2f32d-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f32d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2f32d-105">Syntax</span></span>  
  
```  
HRESULT ExceptionCLRCatcherFound();  
```  
  
## <a name="requirements"></a><span data-ttu-id="2f32d-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2f32d-106">Requirements</span></span>  
 <span data-ttu-id="2f32d-107">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f32d-107">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f32d-108">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2f32d-108">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2f32d-109">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f32d-109">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f32d-110">**.NET framework sürümü:** 1.0</span><span class="sxs-lookup"><span data-stu-id="2f32d-110">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f32d-111">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2f32d-111">See Also</span></span>  
 [<span data-ttu-id="2f32d-112">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="2f32d-112">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2f32d-113">ExceptionCLRCatcherExecute yöntemi</span><span class="sxs-lookup"><span data-stu-id="2f32d-113">ExceptionCLRCatcherExecute Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionclrcatcherexecute-method.md)
