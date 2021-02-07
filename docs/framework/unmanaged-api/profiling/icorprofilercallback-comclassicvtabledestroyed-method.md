---
description: ': ICorProfilerCallback:: Comclassicvtableyok etme yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 91ed5bb65d3a64f1f85a09a710b507974f51c79b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99706389"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="e7993-103">ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7993-103">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>

<span data-ttu-id="e7993-104">Profil oluşturucuyu bir COM birlikte çalışma vtable 'ın yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="e7993-104">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e7993-105">Vtables yok etme işlemi kapanmaya yakın bir şekilde gerçekleştiğinden, bu geri aramanın hiçbir şekilde gerçekleşmemesi olasıdır.</span><span class="sxs-lookup"><span data-stu-id="e7993-105">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7993-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e7993-106">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e7993-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e7993-107">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="e7993-108">\[' de] Bu vtable 'ın oluşturulduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e7993-108">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="e7993-109">\[' de] sınıf tarafından uygulanan arabirimin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="e7993-109">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="e7993-110">Arabirim yalnızca dahili ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="e7993-110">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="e7993-111">\[' de] vtable başlangıcını gösteren bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="e7993-111">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="e7993-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7993-112">Remarks</span></span>  

 <span data-ttu-id="e7993-113">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="e7993-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="e7993-114">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="e7993-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="e7993-115">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="e7993-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7993-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7993-116">Requirements</span></span>  

 <span data-ttu-id="e7993-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7993-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7993-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e7993-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e7993-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="e7993-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e7993-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7993-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7993-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7993-121">See also</span></span>

- [<span data-ttu-id="e7993-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7993-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="e7993-123">COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7993-123">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
