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
ms.openlocfilehash: c4d1f2467927e64ae08c0e7d8067c2ce96b95522
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700216"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="1e5fb-102">ICorProfilerCallback::COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e5fb-102">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>

<span data-ttu-id="1e5fb-103">Profil oluşturucuya, belirtilen IID ve sınıf için bir COM birlikte çalışma vtable 'ın oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-103">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e5fb-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="1e5fb-104">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e5fb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e5fb-105">Parameters</span></span>

- `wrappedClasId`

  <span data-ttu-id="1e5fb-106">\[' de] vtable 'ın oluşturulduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-106">\[in] The ID of the class for which the vtable has been created.</span></span>

- `implementedIID`

  <span data-ttu-id="1e5fb-107">\[' de] sınıf tarafından uygulanan arabirimin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-107">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="1e5fb-108">Arabirim yalnızca dahili ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-108">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="1e5fb-109">\[' de] vtable başlangıcını gösteren bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-109">\[in] A pointer to the start of the vtable.</span></span>

- `cSlots`

  <span data-ttu-id="1e5fb-110">\[' de] vtable 'da olan yuvaların sayısı.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-110">\[in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="1e5fb-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="1e5fb-111">Remarks</span></span>  

 <span data-ttu-id="1e5fb-112">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="1e5fb-113">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="1e5fb-114">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e5fb-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e5fb-115">Requirements</span></span>  

 <span data-ttu-id="1e5fb-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e5fb-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e5fb-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1e5fb-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1e5fb-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="1e5fb-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e5fb-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e5fb-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5fb-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1e5fb-120">See also</span></span>

- [<span data-ttu-id="1e5fb-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e5fb-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="1e5fb-122">COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e5fb-122">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
