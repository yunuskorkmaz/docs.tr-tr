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
ms.openlocfilehash: c04b7862363b441ab35d6dd364c4dffaf7464153
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67769233"
---
# <a name="icorprofilercallbackmoduleloadfinished-method"></a><span data-ttu-id="6f3dd-102">ICorProfilerCallback::ModuleLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f3dd-102">ICorProfilerCallback::ModuleLoadFinished Method</span></span>
<span data-ttu-id="6f3dd-103">Profil Oluşturucu, bir modül yükleme işleminin tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-103">Notifies the profiler that a module has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f3dd-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6f3dd-104">Syntax</span></span>  
  
```cpp  
HRESULT ModuleLoadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6f3dd-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6f3dd-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="6f3dd-106">[in] Yükleme Tamamlandı modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-106">[in] The ID of the module that has finished loading.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="6f3dd-107">[in] Modül başarıyla yüklendi gösteren HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-107">[in] An HRESULT that indicates whether the module was loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6f3dd-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6f3dd-108">Remarks</span></span>  
 <span data-ttu-id="6f3dd-109">Değerini `moduleId` kadar bir bilgi isteği için geçerli değil `ModuleLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-109">The value of `moduleId` is not valid for an information request until the `ModuleLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="6f3dd-110">Modül yükleme bazı bölümleri sonra devam edebilir `ModuleLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-110">Some parts of loading the module might continue after the `ModuleLoadFinished` callback.</span></span> <span data-ttu-id="6f3dd-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6f3dd-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü Modül yükleme işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f3dd-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6f3dd-113">Requirements</span></span>  
 <span data-ttu-id="6f3dd-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f3dd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f3dd-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6f3dd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6f3dd-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f3dd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f3dd-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f3dd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f3dd-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6f3dd-118">See also</span></span>

- [<span data-ttu-id="6f3dd-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6f3dd-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="6f3dd-120">ModuleLoadStarted Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6f3dd-120">ModuleLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleloadstarted-method.md)
