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
ms.openlocfilehash: b9ee87c926d2377ff8eef53f930fe75251b28ceb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137780"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="d0dc0-102">ICorProfilerCallback::AssemblyUnloadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d0dc0-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="d0dc0-103">Profil Oluşturucu, bir derleme kaldırıldı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0dc0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d0dc0-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0dc0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d0dc0-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="d0dc0-106">[in] Boşaltılıyor derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d0dc0-107">[in] Bütünleştirilmiş kod başarıyla kaldırılmış olup olmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0dc0-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d0dc0-108">Remarks</span></span>  
 <span data-ttu-id="d0dc0-109">Değerini `assemblyId` sonra bir bilgi isteği için geçerli değil [Icorprofilercallback::assemblyunloadstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) yöntemi döndürür.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="d0dc0-110">Derleme kaldırılması, bazı bölümleri sonra devam edebilir `AssemblyUnloadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="d0dc0-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d0dc0-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk parçası derleme kaldırma işleminin başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0dc0-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d0dc0-113">Requirements</span></span>  
 <span data-ttu-id="d0dc0-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0dc0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0dc0-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d0dc0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d0dc0-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0dc0-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d0dc0-117">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="d0dc0-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d0dc0-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d0dc0-118">See also</span></span>

- [<span data-ttu-id="d0dc0-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d0dc0-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
