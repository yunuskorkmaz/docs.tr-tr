---
title: ICorProfilerInfo3::GetAppDomainsContainingModule Metodu
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetAppDomainsContainingModule Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetAppDomainsContainingModule
helpviewer_keywords:
- GetAppDomainsContainingModule method [.NET Framework profiling]
- ICorProfilerInfo3::GetAppDomainsContainingModule method [.NET Framework profiling]
ms.assetid: 603b3881-ea94-4dca-95cd-91eebac873a0
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5658ac87c7a938381639442216df03853f02998
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59195793"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="f0669-102">ICorProfilerInfo3::GetAppDomainsContainingModule Metodu</span><span class="sxs-lookup"><span data-stu-id="f0669-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="f0669-103">Belirtilen modül yüklenmiş olan uygulama etki alanları tanımlayıcılarını alır.</span><span class="sxs-lookup"><span data-stu-id="f0669-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0669-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f0669-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0669-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f0669-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="f0669-106">[in] Yüklenen modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="f0669-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="f0669-107">[in] Boyutu `appDomainIds` dizisi.</span><span class="sxs-lookup"><span data-stu-id="f0669-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="f0669-108">[out] Döndürülen öğelerin toplam sayısını bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="f0669-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="f0669-109">[out] Uygulama etki alanı kimliği değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="f0669-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0669-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f0669-110">Remarks</span></span>  
 <span data-ttu-id="f0669-111">Yöntemi arayana ayrılan arabellekler kullanır.</span><span class="sxs-lookup"><span data-stu-id="f0669-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0669-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f0669-112">Requirements</span></span>  
 <span data-ttu-id="f0669-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0669-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0669-114">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f0669-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f0669-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0669-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f0669-116">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="f0669-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f0669-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f0669-117">See also</span></span>

- [<span data-ttu-id="f0669-118">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0669-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="f0669-119">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f0669-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)
- [<span data-ttu-id="f0669-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f0669-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f0669-121">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="f0669-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
