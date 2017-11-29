---
title: ICorProfilerInfo3::GetThreadStaticAddress2 Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location: Mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d657f0d6a28f19c45910fa354b7b40822ad12947
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="4e3c0-102">ICorProfilerInfo3::GetThreadStaticAddress2 Metodu</span><span class="sxs-lookup"><span data-stu-id="4e3c0-102">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>
<span data-ttu-id="4e3c0-103">Belirtilen iş parçacığı ve uygulama etki alanı kapsamında belirtilen statik iş parçacığı alan adresini alır.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-103">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e3c0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e3c0-104">Syntax</span></span>  
  
```  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e3c0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e3c0-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4e3c0-106">[in] İstenen iş parçacığı statik alan içeren sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-106">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="4e3c0-107">[in] İstenen iş parçacığı statik alan için meta veri belirteci.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-107">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="4e3c0-108">[in] Uygulama etki alanı kimliği.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-108">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="4e3c0-109">[in] İstenen statik alanın kapsamı iş parçacığı kimliği.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="4e3c0-110">[out] Belirtilen iş parçacığı içinde statik alan adresini gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e3c0-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e3c0-111">Remarks</span></span>  
 <span data-ttu-id="4e3c0-112">`GetThreadStaticAddress2` Yöntemi döndürebilir şunlardan biri:</span><span class="sxs-lookup"><span data-stu-id="4e3c0-112">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="4e3c0-113">Bir CORPROF_E_DATAINCOMPLETE belirtilen statik alanda belirtilen bağlam bir adres değil atanmışsa HRESULT.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="4e3c0-114">Çöp toplama yığınında olabilir nesneleri adresleri.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="4e3c0-115">Çöp toplama sonra profil oluşturucular geçerli varsayımında bulunmamalıdır şekilde bu adresleri çöp toplama sonra geçersiz hale gelebilir.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="4e3c0-116">Sınıf sınıfı oluşturucusu tamamlanmadan önce `GetThreadStaticAddress2` statik alanları bazıları zaten başlatılmamış olabilir ancak CORPROF_E_DATAINCOMPLETE tüm kendi statik alanları için döndürür ve atık toplama nesneleri kök dizini değiştirme.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-116">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="4e3c0-117">[Icorprofilerınfo2::getthreadstaticaddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) yöntemi benzer `GetThreadStaticAddress2` yöntemi, ancak uygulama etki alanı bağımsız değişken kabul etmiyor.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-117">The [ICorProfilerInfo2::GetThreadStaticAddress](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e3c0-118">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e3c0-118">Requirements</span></span>  
 <span data-ttu-id="4e3c0-119">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e3c0-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e3c0-120">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4e3c0-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4e3c0-121">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e3c0-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e3c0-122">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e3c0-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e3c0-123">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="4e3c0-123">See Also</span></span>  
 [<span data-ttu-id="4e3c0-124">Icorprofilerınfo3 arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e3c0-124">ICorProfilerInfo3 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-interface.md)  
 [<span data-ttu-id="4e3c0-125">Profil oluşturma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4e3c0-125">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="4e3c0-126">Profil oluşturma</span><span class="sxs-lookup"><span data-stu-id="4e3c0-126">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)
