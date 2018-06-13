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
ms.openlocfilehash: e0d560b81aca1c6d859000cda682ee6c75fd7acb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454188"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="a6aa2-102">ICorProfilerInfo3::GetAppDomainsContainingModule Metodu</span><span class="sxs-lookup"><span data-stu-id="a6aa2-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>
<span data-ttu-id="a6aa2-103">Belirtilen modül yüklendi uygulama etki alanları tanımlayıcısını alır.</span><span class="sxs-lookup"><span data-stu-id="a6aa2-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6aa2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a6aa2-104">Syntax</span></span>  
  
```  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6aa2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a6aa2-105">Parameters</span></span>  
 `moduleId`  
 <span data-ttu-id="a6aa2-106">[in] Yüklenen modül kimliği.</span><span class="sxs-lookup"><span data-stu-id="a6aa2-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="a6aa2-107">[in] Boyutunu `appDomainIds` dizi.</span><span class="sxs-lookup"><span data-stu-id="a6aa2-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="a6aa2-108">[out] Döndürülen öğe toplam sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="a6aa2-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="a6aa2-109">[out] Uygulama etki alanı kimliği değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="a6aa2-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6aa2-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a6aa2-110">Remarks</span></span>  
 <span data-ttu-id="a6aa2-111">Yöntemini çağıran arabellekleri ayrılan kullanır.</span><span class="sxs-lookup"><span data-stu-id="a6aa2-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6aa2-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6aa2-112">Requirements</span></span>  
 <span data-ttu-id="a6aa2-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6aa2-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6aa2-114">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6aa2-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6aa2-115">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6aa2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6aa2-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6aa2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6aa2-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="a6aa2-117">See Also</span></span>  
 [<span data-ttu-id="a6aa2-118">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6aa2-118">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)  
 [<span data-ttu-id="a6aa2-119">ICorProfilerInfo3 Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6aa2-119">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="a6aa2-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="a6aa2-120">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="a6aa2-121">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="a6aa2-121">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
