---
description: ': ICorProfilerInfo3:: GetAppDomainsContainingModule yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0f0fea5b01b80b110d7ab041574dc195162cb508
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99646848"
---
# <a name="icorprofilerinfo3getappdomainscontainingmodule-method"></a><span data-ttu-id="fd3af-103">ICorProfilerInfo3::GetAppDomainsContainingModule Metodu</span><span class="sxs-lookup"><span data-stu-id="fd3af-103">ICorProfilerInfo3::GetAppDomainsContainingModule Method</span></span>

<span data-ttu-id="fd3af-104">Verilen modülün yüklendiği uygulama etki alanlarının tanımlayıcılarını alır.</span><span class="sxs-lookup"><span data-stu-id="fd3af-104">Gets the identifiers of the application domains in which the given module has been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd3af-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fd3af-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomainsContainingModule(  
            [in] ModuleID moduleId,  
            [in] ULONG32 cAppDomainIds,  
            [out] ULONG32 *pcAppDomainIds,  
            [out, size_is(cAppDomainIds), length_is(*pcAppDomainIds)]  
                    AppDomainID appDomainIds[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fd3af-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fd3af-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="fd3af-107">'ndaki Yüklenen modülün KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="fd3af-107">[in] The ID of the loaded module.</span></span>  
  
 `cAppDomainIds`  
 <span data-ttu-id="fd3af-108">'ndaki `appDomainIds` Dizinin boyutu.</span><span class="sxs-lookup"><span data-stu-id="fd3af-108">[in] The size of the `appDomainIds` array.</span></span>  
  
 `pcAppDomainIds`  
 <span data-ttu-id="fd3af-109">dışı Döndürülen öğelerin toplam sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="fd3af-109">[out] A pointer to the total number of returned elements.</span></span>  
  
 `appDomainIds`  
 <span data-ttu-id="fd3af-110">dışı Uygulama etki alanı KIMLIĞI değerleri dizisi.</span><span class="sxs-lookup"><span data-stu-id="fd3af-110">[out] An array of application domain ID values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd3af-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fd3af-111">Remarks</span></span>  

 <span data-ttu-id="fd3af-112">Yöntemi, çağıran ayrılmış arabellekleri kullanır.</span><span class="sxs-lookup"><span data-stu-id="fd3af-112">The method uses caller allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd3af-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd3af-113">Requirements</span></span>  

 <span data-ttu-id="fd3af-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd3af-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd3af-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fd3af-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fd3af-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="fd3af-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fd3af-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd3af-117">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd3af-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd3af-118">See also</span></span>

- [<span data-ttu-id="fd3af-119">ICorProfilerFunctionEnum Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd3af-119">ICorProfilerFunctionEnum Interface</span></span>](icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="fd3af-120">ICorProfilerInfo3 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd3af-120">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="fd3af-121">Profil Oluşturma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="fd3af-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="fd3af-122">Profil Oluşturma</span><span class="sxs-lookup"><span data-stu-id="fd3af-122">Profiling</span></span>](index.md)
