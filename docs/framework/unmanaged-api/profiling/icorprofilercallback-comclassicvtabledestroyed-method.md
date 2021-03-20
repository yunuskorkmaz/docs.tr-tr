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
ms.openlocfilehash: e8ed6be2519a9f8959ac4f59313f73f13d6c569b
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760567"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="2a6cd-103">ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a6cd-103">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>

<span data-ttu-id="2a6cd-104">Profil oluşturucuyu bir COM birlikte çalışma vtable 'ın yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-104">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2a6cd-105">Vtables yok etme işlemi kapanmaya yakın bir şekilde gerçekleştiğinden, bu geri aramanın hiçbir şekilde gerçekleşmemesi olasıdır.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-105">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a6cd-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2a6cd-106">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2a6cd-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2a6cd-107">Parameters</span></span>

<span data-ttu-id="2a6cd-108">`wrappedClassId` 'ndaki Bu vtable 'ın oluşturulduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-108">`wrappedClassId` [in] The ID of the class for which this vtable was created.</span></span>

<span data-ttu-id="2a6cd-109">`implementedIID` 'ndaki Sınıf tarafından uygulanan arabirimin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-109">`implementedIID` [in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="2a6cd-110">Arabirim yalnızca dahili ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-110">This value may be NULL if the interface is internal only.</span></span>

<span data-ttu-id="2a6cd-111">`pVTable` 'ndaki Vtable başlangıcına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-111">`pVTable` [in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a6cd-112">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2a6cd-112">Remarks</span></span>  

 <span data-ttu-id="2a6cd-113">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-113">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="2a6cd-114">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-114">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="2a6cd-115">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-115">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2a6cd-116">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2a6cd-116">Requirements</span></span>  

 <span data-ttu-id="2a6cd-117">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2a6cd-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2a6cd-118">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2a6cd-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2a6cd-119">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="2a6cd-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2a6cd-120">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2a6cd-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a6cd-121">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2a6cd-121">See also</span></span>

- [<span data-ttu-id="2a6cd-122">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2a6cd-122">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="2a6cd-123">COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2a6cd-123">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
