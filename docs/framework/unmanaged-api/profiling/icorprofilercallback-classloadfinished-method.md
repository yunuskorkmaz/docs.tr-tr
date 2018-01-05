---
title: "ICorProfilerCallback::ClassLoadFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.ClassLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ae55325f514f9bec3efdf4764958e4b3fafd922b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="bdb56-102">ICorProfilerCallback::ClassLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdb56-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="bdb56-103">Profil Oluşturucu bir sınıf yükleme tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="bdb56-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bdb56-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bdb56-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bdb56-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bdb56-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="bdb56-106">[in] Yüklenen sınıfı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="bdb56-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="bdb56-107">[in] Sınıf başarıyla yüklü olup olmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="bdb56-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bdb56-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bdb56-108">Remarks</span></span>  
 <span data-ttu-id="bdb56-109">Değeri `classId` kadar bilgi isteği için geçerli değil `ClassLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="bdb56-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="bdb56-110">Bazı bölümleri sınıfı yükleme sonrasında devam edebilir `ClassLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="bdb56-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="bdb56-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdb56-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="bdb56-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü sınıfı yükleme başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="bdb56-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bdb56-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bdb56-113">Requirements</span></span>  
 <span data-ttu-id="bdb56-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bdb56-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bdb56-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bdb56-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bdb56-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bdb56-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bdb56-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bdb56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bdb56-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="bdb56-118">See Also</span></span>  
 [<span data-ttu-id="bdb56-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bdb56-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="bdb56-120">ClassLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bdb56-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)
