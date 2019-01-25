---
title: ICorProfilerCallback::ModuleLoadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleLoadFinished
helpviewer_keywords:
- ModuleLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleLoadFinished method [.NET Framework profiling]
ms.assetid: 050649e5-ffc0-4458-a0a4-d9ee128a219e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d15656079c087026a905d9268edf4966d8ef4034
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503566"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="164f6-102">ICorProfilerCallback::ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="164f6-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="164f6-103">Profil Oluşturucu, bir modül yükleme işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="164f6-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="164f6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="164f6-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="164f6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="164f6-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="164f6-106">[in] Yükleme Tamamlandı modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="164f6-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="164f6-107">[in] Modül başarıyla yüklendi gösteren HRESULT.</span><span class="sxs-lookup"><span data-stu-id="164f6-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="164f6-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="164f6-108">Remarks</span></span>  
 <span data-ttu-id="164f6-109">Değerini `moduleId` kadar bir bilgi isteği için geçerli değil `ModuleLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="164f6-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="164f6-110">Modül yükleme bazı bölümleri sonra devam edebilir `ModuleLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="164f6-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="164f6-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="164f6-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="164f6-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü Modül yükleme işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="164f6-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="164f6-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="164f6-113">Requirements</span></span>  
 <span data-ttu-id="164f6-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="164f6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="164f6-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="164f6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="164f6-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="164f6-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="164f6-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="164f6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="164f6-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="164f6-118">See also</span></span>
- [<span data-ttu-id="164f6-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="164f6-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="164f6-120">ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="164f6-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
