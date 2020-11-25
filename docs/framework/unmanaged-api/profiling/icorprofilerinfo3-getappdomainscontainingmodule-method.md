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
ms.openlocfilehash: 5cc3436716bcfc2ed0f9fd7ff7982bac7a48de9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731208"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="8dc5e-102">ICorProfilerInfo3::GetAppDomainsContainingModule Metodu</span><span class="sxs-lookup"><span data-stu-id="8dc5e-102">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>

<span data-ttu-id="8dc5e-103">Verilen modülün yüklendiği uygulama etki alanlarının tanımlayıcılarını alır.</span><span class="sxs-lookup"><span data-stu-id="8dc5e-103">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8dc5e-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8dc5e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8dc5e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8dc5e-105">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="8dc5e-106">'ndaki Yüklenen modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="8dc5e-106">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="8dc5e-107">'ndaki `appDomainIds` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="8dc5e-107">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="8dc5e-108">dışı Döndürülen öğelerin toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8dc5e-108">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="8dc5e-109">dışı Uygulama etki alanı KIMLIĞI değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="8dc5e-109">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dc5e-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8dc5e-110">Remarks</span></span>  

 <span data-ttu-id="8dc5e-111">Yöntemi, çağıran ayrılmış arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="8dc5e-111">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8dc5e-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8dc5e-112">Requirements</span></span>  

 <span data-ttu-id="8dc5e-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8dc5e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8dc5e-114">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8dc5e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8dc5e-115">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="8dc5e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8dc5e-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8dc5e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc5e-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8dc5e-117">See also</span></span>

- [<span data-ttu-id="8dc5e-118">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dc5e-118">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="8dc5e-119">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8dc5e-119">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="8dc5e-120">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="8dc5e-120">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="8dc5e-121">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="8dc5e-121">Profiling</span></span>](index.md)
