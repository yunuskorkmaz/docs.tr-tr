---
title: ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableDestroyed
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed
helpviewer_keywords:
- ICorProfilerCallback::COMClassicVTableDestroyed method [.NET Framework profiling]
- COMClassicVTableDestroyed method [.NET Framework profiling]
ms.assetid: 29da20ca-bf39-4356-8099-d9c3ac3423a9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f60c4373410c46c5d1ea284b2cacd4b5c070ed9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54682829"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="7965a-102">ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7965a-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="7965a-103">Profil Oluşturucu, COM birlikte çalışma vtable edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="7965a-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7965a-104">Vtable yok edilmesini çok yakın bir kapatma işlemi gerçekleşmesi için bu geri çağırma hiçbir zaman oluşma olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="7965a-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7965a-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7965a-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7965a-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7965a-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="7965a-107">[in] Bu vtable oluşturulduğu sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="7965a-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="7965a-108">[in] Sınıfı tarafından uygulanan arabirim kimliği.</span><span class="sxs-lookup"><span data-stu-id="7965a-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="7965a-109">Arabirimi yalnızca iç ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="7965a-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="7965a-110">[in] Vtable başlangıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="7965a-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7965a-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7965a-111">Remarks</span></span>  
 <span data-ttu-id="7965a-112">Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="7965a-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="7965a-113">Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="7965a-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="7965a-114">Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="7965a-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7965a-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7965a-115">Requirements</span></span>  
 <span data-ttu-id="7965a-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7965a-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7965a-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7965a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7965a-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7965a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7965a-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7965a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7965a-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7965a-120">See also</span></span>
- [<span data-ttu-id="7965a-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7965a-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="7965a-122">COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7965a-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
