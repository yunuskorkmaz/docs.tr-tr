---
description: ': ICorProfilerCallback:: COMClassicVTableCreated yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 134ca44cbcd7a275e3ad61a3dd4decaa92668b5b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99657716"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="31f5b-103">ICorProfilerCallback::COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31f5b-103">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>

<span data-ttu-id="31f5b-104">Profil oluşturucuya, belirtilen IID ve sınıf için bir COM birlikte çalışma vtable 'ın oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="31f5b-104">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="31f5b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="31f5b-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="31f5b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="31f5b-106">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="31f5b-107">\[' de] vtable 'ın oluşturulduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="31f5b-107">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="31f5b-108">\[' de] sınıf tarafından uygulanan arabirimin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="31f5b-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="31f5b-109">Arabirim yalnızca dahili ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="31f5b-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="31f5b-110">\[' de] vtable başlangıcını gösteren bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="31f5b-110">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="31f5b-111">\[' de] vtable 'da olan yuvaların sayısı.</span><span class="sxs-lookup"><span data-stu-id="31f5b-111">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="31f5b-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="31f5b-112">Remarks</span></span>  

 <span data-ttu-id="31f5b-113">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="31f5b-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="31f5b-114">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="31f5b-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="31f5b-115">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="31f5b-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="31f5b-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="31f5b-116">Requirements</span></span>  

 <span data-ttu-id="31f5b-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="31f5b-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="31f5b-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="31f5b-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="31f5b-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="31f5b-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="31f5b-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="31f5b-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31f5b-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="31f5b-121">See also</span></span>

- [<span data-ttu-id="31f5b-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="31f5b-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="31f5b-123">COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="31f5b-123">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
