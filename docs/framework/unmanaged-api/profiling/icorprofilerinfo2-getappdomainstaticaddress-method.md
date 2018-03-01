---
title: ICorProfilerInfo2::GetAppDomainStaticAddress Metodu
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2fad6cccc3992f001780bf8bd1a4c879dc6aa754
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="387aa-102">ICorProfilerInfo2::GetAppDomainStaticAddress Metodu</span><span class="sxs-lookup"><span data-stu-id="387aa-102">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>
<span data-ttu-id="387aa-103">Belirtilen uygulama etki alanı kapsamında belirtilen uygulama etki alanı statik alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="387aa-103">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="387aa-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="387aa-104">Syntax</span></span>  
  
```  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="387aa-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="387aa-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="387aa-106">[in] İstenen uygulama etki alanı statik alan içeren sınıf sınıfı kimliği.</span><span class="sxs-lookup"><span data-stu-id="387aa-106">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="387aa-107">[in] İstenen uygulama etki alanı statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="387aa-107">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="387aa-108">[in] İstenen statik alanın kapsamı uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="387aa-108">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="387aa-109">[out] Belirtilen uygulama etki alanı içinde statik alanındaki adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="387aa-109">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="387aa-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="387aa-110">Remarks</span></span>  
 <span data-ttu-id="387aa-111">`GetAppDomainStaticAddress` Yöntemi döndürebilir şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="387aa-111">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="387aa-112">Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanda belirtilen bağlam bir adres değil atanmışsa HRESULT.</span><span class="sxs-lookup"><span data-stu-id="387aa-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="387aa-113">Çöp toplama yığınında olabilir nesneleri adresleri.</span><span class="sxs-lookup"><span data-stu-id="387aa-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="387aa-114">Çöp toplama sonra profil oluşturucular geçerli varsayımında bulunmamalıdır şekilde bu adresleri çöp toplama sonra geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="387aa-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="387aa-115">Sınıf sınıfı oluşturucusu tamamlanmadan önce `GetAppDomainStaticAddress` statik alanları bazıları zaten başlatılmamış olabilir ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür ve atık toplama nesneleri kök dizini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="387aa-115">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="387aa-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="387aa-116">Requirements</span></span>  
 <span data-ttu-id="387aa-117">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="387aa-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="387aa-118">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="387aa-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="387aa-119">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="387aa-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="387aa-120">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="387aa-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="387aa-121">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="387aa-121">See Also</span></span>  
 [<span data-ttu-id="387aa-122">ICorProfilerInfo Arabirimi</span><span class="sxs-lookup"><span data-stu-id="387aa-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="387aa-123">ICorProfilerInfo2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="387aa-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
