---
title: ICorProfilerInfo2::GetContextStaticAddress Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2d206ca90b2d89ead67f419f0f4511d19d8ce110
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="eca9d-102">ICorProfilerInfo2::GetContextStaticAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="eca9d-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="eca9d-103">Belirtilen bağlamı kapsamında belirtilen bağlam statik alan için adresi alır.</span><span class="sxs-lookup"><span data-stu-id="eca9d-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca9d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="eca9d-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eca9d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="eca9d-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="eca9d-106">[in] İstenen içerik statik alan içeren sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="eca9d-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="eca9d-107">[in] İstenen içerik statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="eca9d-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="eca9d-108">[in] İstenen içerik statik alan kapsamı bağlam kimliği.</span><span class="sxs-lookup"><span data-stu-id="eca9d-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="eca9d-109">[out] Belirtilen bağlamı içinde statik alanındaki adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="eca9d-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eca9d-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="eca9d-110">Remarks</span></span>  
 <span data-ttu-id="eca9d-111">`GetContextStaticAddress` Yöntemi döndürebilir şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="eca9d-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="eca9d-112">Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanda belirtilen bağlam bir adres değil atanmışsa HRESULT.</span><span class="sxs-lookup"><span data-stu-id="eca9d-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="eca9d-113">Çöp toplama yığınında olabilir nesneleri adresleri.</span><span class="sxs-lookup"><span data-stu-id="eca9d-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="eca9d-114">Çöp toplama sonra profil oluşturucular geçerli varsayımında bulunmamalıdır şekilde bu adresleri çöp toplama sonra geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="eca9d-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="eca9d-115">Sınıf sınıfı oluşturucusu tamamlanmadan önce `GetContextStaticAddress` statik alanları bazıları zaten başlatılmamış olabilir ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür ve atık toplama nesneleri kök dizini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="eca9d-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eca9d-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="eca9d-116">Requirements</span></span>  
 <span data-ttu-id="eca9d-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eca9d-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eca9d-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="eca9d-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="eca9d-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eca9d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eca9d-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eca9d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eca9d-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="eca9d-121">See Also</span></span>  
 [<span data-ttu-id="eca9d-122">Icorprofilerınfo arabirimi</span><span class="sxs-lookup"><span data-stu-id="eca9d-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="eca9d-123">Icorprofilerınfo2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="eca9d-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
