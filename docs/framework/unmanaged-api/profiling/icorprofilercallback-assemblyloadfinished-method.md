---
title: "ICorProfilerCallback::AssemblyLoadFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af5089603c2044b10061a32c5921b9eeadf86b36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="d89ba-102">ICorProfilerCallback::AssemblyLoadFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d89ba-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="d89ba-103">Profil Oluşturucu bütünleştirilmiş yüklenmesini tamamladı bildirir.</span><span class="sxs-lookup"><span data-stu-id="d89ba-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d89ba-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d89ba-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d89ba-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d89ba-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="d89ba-106">[in] Yüklenen derlemeyi tanımlar.</span><span class="sxs-lookup"><span data-stu-id="d89ba-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="d89ba-107">[in] Derleme yüklemesi başarıyla tamamlandı olup olmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="d89ba-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d89ba-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d89ba-108">Remarks</span></span>  
 <span data-ttu-id="d89ba-109">Değeri `assemblyId` kadar bilgi isteği için geçerli değil `AssemblyLoadFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="d89ba-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="d89ba-110">Derleme yükleme bazı bölümleri sonra devam edebilir `AssemblyLoadFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="d89ba-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="d89ba-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89ba-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="d89ba-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk derlemesi yüklenirken parçası başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="d89ba-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d89ba-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d89ba-113">Requirements</span></span>  
 <span data-ttu-id="d89ba-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d89ba-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d89ba-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d89ba-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d89ba-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d89ba-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d89ba-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d89ba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d89ba-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d89ba-118">See Also</span></span>  
 [<span data-ttu-id="d89ba-119">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="d89ba-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
