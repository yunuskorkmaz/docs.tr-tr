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
ms.openlocfilehash: 04ba37b9c1307539c9fdf299f4667e7026d571be
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760580"
---
# <a name="icorprofilercallbackcomclassicvtablecreated-method"></a><span data-ttu-id="b0038-103">ICorProfilerCallback::COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0038-103">ICorProfilerCallback::COMClassicVTableCreated Method</span></span>

<span data-ttu-id="b0038-104">Profil oluşturucuya, belirtilen IID ve sınıf için bir COM birlikte çalışma vtable 'ın oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="b0038-104">Notifies the profiler that a COM interop vtable for the specified IID and class has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0038-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b0038-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableCreated(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable,  
    [in] ULONG   cSlots);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0038-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b0038-106">Parameters</span></span>

<span data-ttu-id="b0038-107">`wrappedClasId` 'ndaki Vtable 'ın oluşturulduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b0038-107">`wrappedClasId` [in] The ID of the class for which the vtable has been created.</span></span>

<span data-ttu-id="b0038-108">`implementedIID` 'ndaki Sınıf tarafından uygulanan arabirimin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="b0038-108">`implementedIID` [in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="b0038-109">Arabirim yalnızca dahili ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="b0038-109">This value may be NULL if the interface is internal only.</span></span>

<span data-ttu-id="b0038-110">`pVTable` 'ndaki Vtable başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="b0038-110">`pVTable` [in] A pointer to the start of the vtable.</span></span>

<span data-ttu-id="b0038-111">`cSlots` 'ndaki Vtable 'daki yuva sayısı.</span><span class="sxs-lookup"><span data-stu-id="b0038-111">`cSlots` [in] The number of slots that are in the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="b0038-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b0038-112">Remarks</span></span>  

 <span data-ttu-id="b0038-113">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="b0038-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="b0038-114">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="b0038-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="b0038-115">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="b0038-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0038-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b0038-116">Requirements</span></span>  

 <span data-ttu-id="b0038-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0038-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0038-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b0038-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b0038-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="b0038-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0038-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0038-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0038-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b0038-121">See also</span></span>

- [<span data-ttu-id="b0038-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b0038-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="b0038-123">COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b0038-123">COMClassicVTableDestroyed Method</span></span>](icorprofilercallback-comclassicvtabledestroyed-method.md)
