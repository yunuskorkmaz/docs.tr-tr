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
ms.openlocfilehash: 14f918a312031359043076be0b739f9b7e0e9f2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451649"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="2324a-102">ICorProfilerCallback::ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2324a-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="2324a-103">Profil Oluşturucu bir modül yüklenmesini tamamladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="2324a-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2324a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2324a-104">Syntax</span></span>  
  
```  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2324a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2324a-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="2324a-106">[in] Yükleme Tamamlandı modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="2324a-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="2324a-107">[in] Modül başarıyla yüklü olup olmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="2324a-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2324a-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2324a-108">Remarks</span></span>  
 <span data-ttu-id="2324a-109">Değeri `moduleId` kadar bilgi isteği için geçerli değil `ModuleLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2324a-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="2324a-110">Modül yükleme bazı bölümleri sonra devam edebilir `ModuleLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="2324a-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="2324a-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="2324a-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="2324a-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü modülü yükleme başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="2324a-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2324a-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2324a-113">Requirements</span></span>  
 <span data-ttu-id="2324a-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2324a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2324a-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2324a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2324a-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2324a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2324a-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2324a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2324a-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2324a-118">See Also</span></span>  
 [<span data-ttu-id="2324a-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2324a-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="2324a-120">ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2324a-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
