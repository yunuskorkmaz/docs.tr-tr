---
title: ICorProfilerCallback::AppDomainCreationFinished Yöntemi
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AppDomainCreationFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type:
- apiref
ms.openlocfilehash: 8b3f7712436c001e5cd44f214f6edb06390abd41
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177078"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="6dd8f-102">ICorProfilerCallback::AppDomainCreationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6dd8f-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="6dd8f-103">Profil oluşturucuya bir uygulama etki alanı oluşturulduğunu belirtir.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6dd8f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6dd8f-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="6dd8f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6dd8f-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="6dd8f-106">\[in] Oluşturulan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="6dd8f-107">\[in] Uygulama etki alanıoluşturmanın başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="6dd8f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6dd8f-108">Remarks</span></span>  
 <span data-ttu-id="6dd8f-109">`AppDomainCreationFinished` Yöntem çağrılana kadar başvuru kimliği herhangi bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="6dd8f-110">Uygulama etki alanıyüklemenin bazı bölümleri `AppDomainCreationFinished` geri aramadan sonra da devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="6dd8f-111">Bir hata HRESULT bir hata `hrStatus` gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="6dd8f-112">Ancak, bir başarı `hrStatus` HRESULT yalnızca uygulama etki alanı oluşturma nın ilk bölümü başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6dd8f-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6dd8f-113">Requirements</span></span>  
 <span data-ttu-id="6dd8f-114">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6dd8f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6dd8f-115">**Üstbilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6dd8f-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6dd8f-116">**Kütüphane:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6dd8f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6dd8f-117">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dd8f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dd8f-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6dd8f-118">See also</span></span>

- [<span data-ttu-id="6dd8f-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6dd8f-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
