---
title: "ICorProfilerCallback::AssemblyLoadFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9de280a1b92bc921ecb400c80522f21cf65f861a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="c78f1-102">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c78f1-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="c78f1-103">Profil Oluşturucu bütünleştirilmiş yüklenmesini tamamladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="c78f1-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c78f1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c78f1-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c78f1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c78f1-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="c78f1-106">[in] Yüklenen derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c78f1-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c78f1-107">[in] Derleme yüklemesi başarıyla tamamlandı olup olmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c78f1-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c78f1-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c78f1-108">Remarks</span></span>  
 <span data-ttu-id="c78f1-109">Değeri `assemblyId` kadar bilgi isteği için geçerli değil `AssemblyLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c78f1-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="c78f1-110">Derleme yükleme bazı bölümleri sonra devam edebilir `AssemblyLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="c78f1-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="c78f1-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="c78f1-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c78f1-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk derlemesi yüklenirken parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c78f1-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c78f1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c78f1-113">Requirements</span></span>  
 <span data-ttu-id="c78f1-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c78f1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c78f1-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c78f1-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c78f1-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c78f1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c78f1-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c78f1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c78f1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c78f1-118">See Also</span></span>  
 [<span data-ttu-id="c78f1-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c78f1-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
