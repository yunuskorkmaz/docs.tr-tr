---
title: "ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.COMClassicVTableDestroyed
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: ebff8297a708b130a0d3983fd75b76c3aeaeceaf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="6c157-102">ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c157-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="6c157-103">Profil Oluşturucu COM birlikte çalışma vtable yok olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6c157-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c157-104">Vtable edilmesine çok yakın kapatma oluştuğundan bu geri çağırma asla meydana olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="6c157-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c157-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6c157-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6c157-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6c157-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="6c157-107">[in] Bu vtable oluşturulduğu sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c157-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="6c157-108">[in] Sınıfı tarafından uygulanan arabirimi kimliği.</span><span class="sxs-lookup"><span data-stu-id="6c157-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="6c157-109">Arabirimi yalnızca iç ise bu değeri NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="6c157-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="6c157-110">[in] Bir işaretçi vtable başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="6c157-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c157-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6c157-111">Remarks</span></span>  
 <span data-ttu-id="6c157-112">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="6c157-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="6c157-113">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="6c157-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="6c157-114">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="6c157-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c157-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6c157-115">Requirements</span></span>  
 <span data-ttu-id="6c157-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c157-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c157-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6c157-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c157-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6c157-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c157-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c157-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c157-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6c157-120">See Also</span></span>  
 [<span data-ttu-id="6c157-121">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="6c157-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="6c157-122">COMClassicVTableCreated yöntemi</span><span class="sxs-lookup"><span data-stu-id="6c157-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
