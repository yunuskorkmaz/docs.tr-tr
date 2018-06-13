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
ms.openlocfilehash: 30d1e80d05344448c19c9f8f2d261442e4041487
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33451723"
---
# <a name="icorprofilercallbackcomclassicvtabledestroyed-method"></a><span data-ttu-id="41267-102">ICorProfilerCallback::COMClassicVTableDestroyed Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41267-102">ICorProfilerCallback::COMClassicVTableDestroyed Method</span></span>
<span data-ttu-id="41267-103">Profil Oluşturucu COM birlikte çalışma vtable yok olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="41267-103">Notifies the profiler that a COM interop vtable is being destroyed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41267-104">Vtable edilmesine çok yakın kapatma oluştuğundan bu geri çağırma asla meydana olasılığı yüksektir.</span><span class="sxs-lookup"><span data-stu-id="41267-104">This callback is likely never to occur, because the destruction of vtables occurs very close to shutdown.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41267-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="41267-105">Syntax</span></span>  
  
```  
HRESULT COMClassicVTableDestroyed(  
    [in] ClassID wrappedClassId,  
    [in] REFGUID implementedIID,  
    [in] void    *pVTable);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="41267-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="41267-106">Parameters</span></span>  
 `wrappedClasId`  
 <span data-ttu-id="41267-107">[in] Bu vtable oluşturulduğu sınıf kimliği.</span><span class="sxs-lookup"><span data-stu-id="41267-107">[in] The ID of the class for which this vtable was created.</span></span>  
  
 `implementedIID`  
 <span data-ttu-id="41267-108">[in] Sınıfı tarafından uygulanan arabirimi kimliği.</span><span class="sxs-lookup"><span data-stu-id="41267-108">[in] The ID of the interface implemented by the class.</span></span> <span data-ttu-id="41267-109">Arabirimi yalnızca iç ise bu değeri NULL olabilir.</span><span class="sxs-lookup"><span data-stu-id="41267-109">This value may be NULL if the interface is internal only.</span></span>  
  
 `pVTable`  
 <span data-ttu-id="41267-110">[in] Bir işaretçi vtable başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="41267-110">[in] A pointer to the start of the vtable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41267-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="41267-111">Remarks</span></span>  
 <span data-ttu-id="41267-112">Yığın çöp toplama izin veren bir durumda olmayabileceğinden profil oluşturucu, bu yöntem uygulamasında engelleyebilir miyim değil ve bu nedenle PreEmptive tarafından çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="41267-112">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="41267-113">Profil Oluşturucu burada engelliyorsa ve atık toplama denemesi, bu geri çağırma dönene kadar çalışma zamanı engeller.</span><span class="sxs-lookup"><span data-stu-id="41267-113">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="41267-114">Bu yöntemin kullanımı Profil Oluşturucu'nın yönetilen koda veya herhangi bir yönetilen bellek ayırma şekilde neden çağırmalıdır değil.</span><span class="sxs-lookup"><span data-stu-id="41267-114">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41267-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="41267-115">Requirements</span></span>  
 <span data-ttu-id="41267-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41267-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41267-117">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="41267-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="41267-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41267-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41267-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41267-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41267-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="41267-120">See Also</span></span>  
 [<span data-ttu-id="41267-121">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="41267-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="41267-122">COMClassicVTableCreated Yöntemi</span><span class="sxs-lookup"><span data-stu-id="41267-122">COMClassicVTableCreated Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-comclassicvtablecreated-method.md)
