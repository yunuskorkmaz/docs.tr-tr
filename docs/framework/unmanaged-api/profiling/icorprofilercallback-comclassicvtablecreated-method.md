---
title: ICorProfilerCallback::COMClassicVTableCreated Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.COMClassicVTableCreated
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::COMClassicVTableCreated
helpviewer_keywords:
- COMClassicVTableCreated method [.NET Framework profiling]
- ICorProfilerCallback::COMClassicVTableCreated method [.NET Framework profiling]
ms.assetid: 6e1834ab-c359-498a-b10b-984ae23cdda4
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2dcb45fcc987952ec5e84cc468dda8d8ede38bdf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451317"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="0244d-102">ICorProfilerCallback::COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0244d-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="0244d-103">Profil Oluşturucu belirtilen IID ve sınıf için bir COM birlikte çalışma vtable oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="0244d-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0244d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0244d-104">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0244d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0244d-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="0244d-106">[in] Vtable oluşturulan sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="0244d-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="0244d-107">[in] Sınıfı tarafından uygulanan arabirimi kimliği.</span><span class="sxs-lookup"><span data-stu-id="0244d-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="0244d-108">Arabirimi yalnızca iç ise bu değeri NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="0244d-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="0244d-109">[in] Bir işaretçi vtable başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="0244d-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="0244d-110">[in] Vtable olan yuva sayısı.</span><span class="sxs-lookup"><span data-stu-id="0244d-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0244d-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0244d-111">Remarks</span></span>  
 <span data-ttu-id="0244d-112">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="0244d-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="0244d-113">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="0244d-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="0244d-114">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="0244d-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0244d-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0244d-115">Requirements</span></span>  
 <span data-ttu-id="0244d-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0244d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0244d-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0244d-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0244d-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0244d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0244d-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0244d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0244d-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0244d-120">See Also</span></span>  
 [<span data-ttu-id="0244d-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0244d-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="0244d-122">COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0244d-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
