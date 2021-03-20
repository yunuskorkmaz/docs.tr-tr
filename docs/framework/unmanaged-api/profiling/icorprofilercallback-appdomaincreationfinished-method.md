---
description: ': ICorProfilerCallback:: AppDomainCreationFinished Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 51ed9ba19d96fd6ea05d05b07fe329aa9c01f290
ms.sourcegitcommit: 20b4565974d185c7716656a6c63e3cfdbdf4bf41
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/20/2021
ms.locfileid: "104760762"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="5ee9d-103">ICorProfilerCallback::AppDomainCreationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ee9d-103">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>

<span data-ttu-id="5ee9d-104">Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5ee9d-104">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee9d-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5ee9d-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="5ee9d-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5ee9d-106">Parameters</span></span>

<span data-ttu-id="5ee9d-107">`appDomainId` 'ndaki Oluşturulan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5ee9d-107">`appDomainId` [in] Identifies the domain which has been created.</span></span>

<span data-ttu-id="5ee9d-108">`hrStatus` 'ndaki Uygulama etki alanı oluşturma 'nın başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5ee9d-108">`hrStatus` [in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ee9d-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ee9d-109">Remarks</span></span>  

 <span data-ttu-id="5ee9d-110">Uygulama KIMLIĞI, yöntem çağrılana kadar herhangi bir bilgi isteği için geçerli değildir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="5ee9d-110">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="5ee9d-111">Uygulama etki alanını yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="5ee9d-111">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="5ee9d-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ee9d-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="5ee9d-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca uygulama etki alanı oluşturmanın ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5ee9d-113">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ee9d-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ee9d-114">Requirements</span></span>  

 <span data-ttu-id="5ee9d-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ee9d-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ee9d-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5ee9d-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5ee9d-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5ee9d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5ee9d-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ee9d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ee9d-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ee9d-119">See also</span></span>

- [<span data-ttu-id="5ee9d-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ee9d-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
