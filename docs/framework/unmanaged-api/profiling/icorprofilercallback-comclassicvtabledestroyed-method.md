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
ms.openlocfilehash: 708981155589d491a3b1819adb611a28072dd1bf
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500331"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="07e18-102">ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07e18-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="07e18-103">Profil oluşturucuyu bir COM birlikte çalışma vtable 'ın yok edildiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="07e18-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07e18-104">Vtables yok etme işlemi kapanmaya yakın bir şekilde gerçekleştiğinden, bu geri aramanın hiçbir şekilde gerçekleşmemesi olasıdır.</span><span class="sxs-lookup"><span data-stu-id="07e18-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="07e18-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="07e18-105">Syntax</span></span>  
  
```cpp  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="07e18-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="07e18-106">Parameters</span></span>

- `wrappedClassId`

  <span data-ttu-id="07e18-107">\[' de] Bu vtable 'ın oluşturulduğu sınıfın KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07e18-107">\[in] The ID of the class for which this vtable was created.</span></span>

- `implementedIID`

  <span data-ttu-id="07e18-108">\[' de] sınıf tarafından uygulanan arabirimin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="07e18-108">\[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="07e18-109">Arabirim yalnızca dahili ise bu değer NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="07e18-109">This value may be NULL if the interface is internal only.</span></span>

- `pVTable`

  <span data-ttu-id="07e18-110">\[' de] vtable başlangıcını gösteren bir işaretçidir.</span><span class="sxs-lookup"><span data-stu-id="07e18-110">\[in] A pointer to the start of the vtable.</span></span>

## <a name="remarks"></a><span data-ttu-id="07e18-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="07e18-111">Remarks</span></span>  
 <span data-ttu-id="07e18-112">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="07e18-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="07e18-113">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="07e18-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="07e18-114">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="07e18-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07e18-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="07e18-115">Requirements</span></span>  
 <span data-ttu-id="07e18-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07e18-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07e18-117">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="07e18-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07e18-118">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="07e18-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07e18-119">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07e18-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07e18-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="07e18-120">See also</span></span>

- [<span data-ttu-id="07e18-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="07e18-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="07e18-122">COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="07e18-122">COMClassicVTableCreated Method</span></span>](icorprofilercallback-comclassicvtablecreated-method.md)
