---
title: ICorProfilerCallback::AssemblyUnloadFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a6a9fe86d6160ebac084625ef94013cce9a27a3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501886"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="60078-102">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="60078-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="60078-103">Profil Oluşturucu, bir derleme kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="60078-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="60078-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="60078-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="60078-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="60078-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="60078-106">[in] Boşaltılıyor derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="60078-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="60078-107">[in] Bütünleştirilmiş kod başarıyla kaldırılmış olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="60078-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="60078-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="60078-108">Remarks</span></span>  
 <span data-ttu-id="60078-109">Değerini `assemblyId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="60078-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="60078-110">Derleme kaldırılması, bazı bölümleri sonra devam edebilir `AssemblyUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="60078-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="60078-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="60078-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="60078-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk parçası derleme kaldırma işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="60078-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="60078-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="60078-113">Requirements</span></span>  
 <span data-ttu-id="60078-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60078-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="60078-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="60078-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="60078-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60078-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="60078-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60078-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60078-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="60078-118">See also</span></span>
- [<span data-ttu-id="60078-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="60078-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
