---
title: ICorProfilerInfo3::GetAppDomainsContainingModule Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa0aa6620f8465154ac31586618af3fe36f3dfe4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="3a6e7-102">ICorProfilerInfo3::GetAppDomainsContainingModule Metodu</span><span class="sxs-lookup"><span data-stu-id="3a6e7-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="3a6e7-103">Belirtilen modül yüklendi uygulama etki alanları tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="3a6e7-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a6e7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3a6e7-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3a6e7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3a6e7-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="3a6e7-106">[in] Yüklenen modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="3a6e7-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="3a6e7-107">[in] Boyutunu `appDomainIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="3a6e7-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="3a6e7-108">[out] Döndürülen öğe toplam sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="3a6e7-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="3a6e7-109">[out] Uygulama etki alanı kimliği değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="3a6e7-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a6e7-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3a6e7-110">Remarks</span></span>  
 <span data-ttu-id="3a6e7-111">Yöntemini çağıran arabellekleri ayrılan kullanır.</span><span class="sxs-lookup"><span data-stu-id="3a6e7-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a6e7-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3a6e7-112">Requirements</span></span>  
 <span data-ttu-id="3a6e7-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a6e7-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a6e7-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3a6e7-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a6e7-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a6e7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a6e7-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a6e7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a6e7-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3a6e7-117">See Also</span></span>  
 [<span data-ttu-id="3a6e7-118">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3a6e7-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="3a6e7-119">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3a6e7-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="3a6e7-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3a6e7-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="3a6e7-121">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="3a6e7-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
