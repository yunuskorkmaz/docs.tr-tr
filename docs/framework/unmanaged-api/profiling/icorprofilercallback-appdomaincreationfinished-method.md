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
ms.openlocfilehash: eaf0ae2a1b86234495c1804cff8b74331b3e8021
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445279"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="c4ff8-102">ICorProfilerCallback::AppDomainCreationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c4ff8-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="c4ff8-103">Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4ff8-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c4ff8-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="c4ff8-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c4ff8-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="c4ff8-106">'ndaki Oluşturulan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c4ff8-107">'ndaki Uygulama etki alanı oluşturma 'nın başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c4ff8-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c4ff8-108">Remarks</span></span>  
 <span data-ttu-id="c4ff8-109">`AppDomainCreationFinished` yöntemi çağrılana kadar, uygulama KIMLIĞI herhangi bir bilgi isteği için geçerli değildir.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="c4ff8-110">Uygulama etki alanını yüklemenin bazı bölümleri `AppDomainCreationFinished` geri çağrısından sonra devam edebilir.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="c4ff8-111">`hrStatus` HRESULT hatası, bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c4ff8-112">Ancak `hrStatus` başarılı bir HRESULT, yalnızca uygulama etki alanı oluşturmanın ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4ff8-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c4ff8-113">Requirements</span></span>  
 <span data-ttu-id="c4ff8-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4ff8-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4ff8-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c4ff8-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c4ff8-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="c4ff8-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4ff8-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4ff8-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4ff8-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c4ff8-118">See also</span></span>

- [<span data-ttu-id="c4ff8-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c4ff8-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
