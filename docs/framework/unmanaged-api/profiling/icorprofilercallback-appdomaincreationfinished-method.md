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
ms.openlocfilehash: 6995c6cda168b5be5815e6f7b2b4d900ae0d4d67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99648369"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="5df82-103">ICorProfilerCallback::AppDomainCreationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5df82-103">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>

<span data-ttu-id="5df82-104">Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5df82-104">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5df82-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="5df82-105">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="5df82-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5df82-106">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="5df82-107">\[' de], oluşturulan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="5df82-107">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="5df82-108">\[içinde] uygulama etki alanının oluşturulmasını başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="5df82-108">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="5df82-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5df82-109">Remarks</span></span>  

 <span data-ttu-id="5df82-110">Uygulama KIMLIĞI, yöntem çağrılana kadar herhangi bir bilgi isteği için geçerli değildir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="5df82-110">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="5df82-111">Uygulama etki alanını yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="5df82-111">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="5df82-112">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="5df82-112">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="5df82-113">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca uygulama etki alanı oluşturmanın ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="5df82-113">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5df82-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5df82-114">Requirements</span></span>  

 <span data-ttu-id="5df82-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5df82-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5df82-116">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5df82-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5df82-117">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="5df82-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5df82-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5df82-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5df82-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5df82-119">See also</span></span>

- [<span data-ttu-id="5df82-120">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5df82-120">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
