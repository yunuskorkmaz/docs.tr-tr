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
ms.openlocfilehash: 062b63776264ae553039a2db0fc99d4fb7bec476
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67745332"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="51339-102">ICorProfilerCallback::COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51339-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>
<span data-ttu-id="51339-103">Profil Oluşturucu, belirtilen IID ve sınıfı bir COM birlikte çalışma vtable oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="51339-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51339-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="51339-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51339-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="51339-105">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="51339-106">[in] Vtable oluşturulan sınıfın Kimliğidir.</span><span class="sxs-lookup"><span data-stu-id="51339-106">[in] The ID of the class for which the vtable has been created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="51339-107">[in] Sınıfı tarafından uygulanan arabirim kimliği.</span><span class="sxs-lookup"><span data-stu-id="51339-107">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="51339-108">Arabirimi yalnızca iç ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="51339-108">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="51339-109">[in] Vtable başlangıcı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="51339-109">[in] A pointer to the start of the vtable.</span></span>  
  
 `cSlots`  
 <span data-ttu-id="51339-110">[in] Vtable içinde olan yuva sayısı.</span><span class="sxs-lookup"><span data-stu-id="51339-110">[in] The number of slots that are in the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51339-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="51339-111">Remarks</span></span>  
 <span data-ttu-id="51339-112">Yığın atık toplama izin veren bir durumda olmayabilir çünkü profil oluşturucu bu yöntemin uygulanması Engellemesi gereken değil ve bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="51339-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="51339-113">Burada profil oluşturucu engellerse ve çöp toplama denenir, çalışma zamanı, bu geri dönene kadar engeller.</span><span class="sxs-lookup"><span data-stu-id="51339-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="51339-114">Bu yöntemin uygulanmasını profil oluşturucunun yönetilen koda veya herhangi bir yönetilen bellek ayırma yol neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="51339-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51339-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="51339-115">Requirements</span></span>  
 <span data-ttu-id="51339-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51339-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51339-117">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="51339-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="51339-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51339-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51339-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51339-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51339-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="51339-120">See also</span></span>

- [<span data-ttu-id="51339-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="51339-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="51339-122">COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="51339-122">COMClassicVTableDestroyed Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtabledestroyed-method.md)
