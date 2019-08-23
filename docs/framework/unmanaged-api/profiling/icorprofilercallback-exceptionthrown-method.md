---
title: ICorProfilerCallback::ExceptionThrown Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01e407b726ce4426f3b58bc29854b30bd6add257
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953870"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="c0a69-102">ICorProfilerCallback::ExceptionThrown Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c0a69-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="c0a69-103">Profiler öğesine bir özel durum gerçekleştiğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="c0a69-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c0a69-104">Bu işlev yalnızca özel durum yönetilen koda ulaşırsa çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c0a69-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a69-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c0a69-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0a69-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c0a69-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="c0a69-107">'ndaki Özel duruma neden olan nesnenin KIMLIĞI.</span><span class="sxs-lookup"><span data-stu-id="c0a69-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c0a69-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c0a69-108">Remarks</span></span>  
 <span data-ttu-id="c0a69-109">Yığın atık toplamaya izin veren bir durumda olmadığından profil oluşturucu bu yöntemin uygulamasında engellenmemelidir, bu nedenle preemptive çöp toplama etkinleştirilemez.</span><span class="sxs-lookup"><span data-stu-id="c0a69-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="c0a69-110">Profil Oluşturucu burada ve çöp toplama denendiğinde, bu geri arama dönene kadar çalışma zamanı engellenir.</span><span class="sxs-lookup"><span data-stu-id="c0a69-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="c0a69-111">Profil oluşturucunun bu yöntemin uygulanması yönetilen koda veya herhangi bir şekilde bir yönetilen bellek ayırmaya yol açmaz.</span><span class="sxs-lookup"><span data-stu-id="c0a69-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0a69-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c0a69-112">Requirements</span></span>  
 <span data-ttu-id="c0a69-113">**Platform** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0a69-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0a69-114">**Üst bilgi** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c0a69-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c0a69-115">**Kitaplığı** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c0a69-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0a69-116">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0a69-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0a69-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c0a69-117">See also</span></span>

- [<span data-ttu-id="c0a69-118">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c0a69-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
