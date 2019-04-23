---
title: ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2095f02cb23c3580b0a1109e8f0da669f61adabc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59098701"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="1f696-102">ICorProfilerInfo2::GetAppDomainStaticAddress Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f696-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="1f696-103">Belirtilen uygulama etki alanı kapsamı içinde belirtilen uygulama etki alanı statik alanı adresini alır.</span><span class="sxs-lookup"><span data-stu-id="1f696-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f696-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1f696-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f696-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1f696-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="1f696-106">[in] İstenen uygulama etki alanı statik alanı içeren sınıf sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="1f696-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="1f696-107">[in] İstenen uygulama etki alanı statik alanı için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="1f696-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="1f696-108">[in] İstenen statik alan için kapsamı uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="1f696-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="1f696-109">[out] Belirtilen uygulama etki alanı içinde statik alanı adresi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1f696-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f696-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1f696-110">Remarks</span></span>  
 <span data-ttu-id="1f696-111">`GetAppDomainStaticAddress` Yöntemi aşağıdakilerden birini döndürebilir:</span><span class="sxs-lookup"><span data-stu-id="1f696-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="1f696-112">Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanı belirtilen bağlam bir adres değil atandıysa HRESULT.</span><span class="sxs-lookup"><span data-stu-id="1f696-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="1f696-113">Adresleri nesnelerin çöp koleksiyonu yığınında olabilir.</span><span class="sxs-lookup"><span data-stu-id="1f696-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="1f696-114">Çöp toplamanın ardından, profil oluşturucular geçerli olduğunu varsayın değil için bu adresleri çöp toplamanın ardından geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="1f696-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="1f696-115">Bir sınıfın sınıf oluşturucusu tamamlanmadan önce `GetAppDomainStaticAddress` bazı statik alanlar zaten başlatılmış olabilir ancak tüm kendi statik alanları için CORPROF_E_DATAINCOMPLETE döndürür ve çöp toplama nesneleri kök dizini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="1f696-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f696-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f696-116">Requirements</span></span>  
 <span data-ttu-id="1f696-117">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f696-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f696-118">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f696-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f696-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f696-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f696-120">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f696-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f696-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1f696-121">See also</span></span>

- [<span data-ttu-id="1f696-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f696-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="1f696-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f696-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
