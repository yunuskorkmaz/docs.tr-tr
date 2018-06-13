---
title: ICorProfilerCallback::ModuleUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ModuleUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ModuleUnloadFinished
helpviewer_keywords:
- ModuleUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ModuleUnloadFinished method [.NET Framework profiling]
ms.assetid: 185e3327-9f9c-44bc-8a5c-febea9a6bb5b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5a4637ac7466a575c94f8244168576c4a5542689
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452094"
---
# <a name="icorprofilercallbackmoduleunloadfinished-method"></a><span data-ttu-id="45579-102">ICorProfilerCallback::ModuleUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45579-102">ICorProfilerCallback::ModuleUnloadFinished Method</span></span>
<span data-ttu-id="45579-103">Profil Oluşturucu bir modül kaldırılması tamamlandığını bildirir.</span><span class="sxs-lookup"><span data-stu-id="45579-103">Notifies the profiler that a module has finished unloading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45579-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45579-104">Syntax</span></span>  
  
```  
HRESULT ModuleUnloadFinished(  
    [in] ModuleID moduleId,  
    [in] HRESULT  hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45579-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45579-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="45579-106">[in] Kaldırıldı modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="45579-106">[in] The ID of the module that was unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="45579-107">[in] Modül başarıyla kaldırıldı olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="45579-107">[in] An HRESULT that indicates whether the module was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45579-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45579-108">Remarks</span></span>  
 <span data-ttu-id="45579-109">Değeri `moduleId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::moduleunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="45579-109">The value of `moduleId` is not valid for an information request after the [ICorProfilerCallback::ModuleUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-moduleunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="45579-110">Sınıf kaldırılması, bazı bölümleri sonra devam edebilir `ModuleUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="45579-110">Some parts of unloading the class might continue after the `ModuleUnloadFinished` callback.</span></span> <span data-ttu-id="45579-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="45579-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="45579-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk modülü kaldırılması parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="45579-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the module has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45579-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45579-113">Requirements</span></span>  
 <span data-ttu-id="45579-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45579-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45579-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45579-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45579-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45579-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45579-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45579-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45579-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="45579-118">See Also</span></span>  
 [<span data-ttu-id="45579-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45579-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
