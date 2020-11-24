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
ms.openlocfilehash: 688b9975cc68463de066e5225c6ab1e04cbb5337
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95685389"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="045f5-102">ICorProfilerCallback::AppDomainCreationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="045f5-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>

<span data-ttu-id="045f5-103">Profil oluşturucuyu bir uygulama etki alanının oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="045f5-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045f5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="045f5-104">Syntax</span></span>  
  
```cpp  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);
```  
  
## <a name="parameters"></a><span data-ttu-id="045f5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="045f5-105">Parameters</span></span>

- `appDomainId`

  <span data-ttu-id="045f5-106">\[' de], oluşturulan etki alanını tanımlar.</span><span class="sxs-lookup"><span data-stu-id="045f5-106">\[in] Identifies the domain which has been created.</span></span>

- `hrStatus`

  <span data-ttu-id="045f5-107">\[içinde] uygulama etki alanının oluşturulmasını başarıyla tamamlanıp tamamlanmadığını gösteren bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="045f5-107">\[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="045f5-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="045f5-108">Remarks</span></span>  

 <span data-ttu-id="045f5-109">Uygulama KIMLIĞI, yöntem çağrılana kadar herhangi bir bilgi isteği için geçerli değildir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="045f5-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="045f5-110">Uygulama etki alanını yüklemenin bazı bölümleri geri aramadan sonra devam edebilir `AppDomainCreationFinished` .</span><span class="sxs-lookup"><span data-stu-id="045f5-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="045f5-111">' De HRESULT hatası, `hrStatus` bir hatayı gösterir.</span><span class="sxs-lookup"><span data-stu-id="045f5-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="045f5-112">Ancak, içinde başarılı bir HRESULT, `hrStatus` yalnızca uygulama etki alanı oluşturmanın ilk bölümünün başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="045f5-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="045f5-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="045f5-113">Requirements</span></span>  

 <span data-ttu-id="045f5-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="045f5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="045f5-115">**Üst bilgi:** CorProf. IDL, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="045f5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="045f5-116">**Kitaplık:** Corguid. lib</span><span class="sxs-lookup"><span data-stu-id="045f5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="045f5-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="045f5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045f5-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="045f5-118">See also</span></span>

- [<span data-ttu-id="045f5-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="045f5-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
