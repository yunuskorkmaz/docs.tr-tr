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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a08a0ed8303804df1889973fe3ffab6db93249d5
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57481450"
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="395bc-102">ICorProfilerCallback::AppDomainCreationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="395bc-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="395bc-103">Profil Oluşturucu, bir uygulama etki alanı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="395bc-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="395bc-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="395bc-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
## <a name="parameters"></a><span data-ttu-id="395bc-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="395bc-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="395bc-106">[in] Oluşturulan etki alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="395bc-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="395bc-107">[in] Uygulama etki alanı oluşturulmasını başarıyla tamamlanıp tamamlanmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="395bc-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="395bc-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="395bc-108">Remarks</span></span>  
 <span data-ttu-id="395bc-109">Uygulama Kimliği kadar herhangi bir bilgi isteği için geçerli değil. `AppDomainCreationFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="395bc-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="395bc-110">Uygulama etki alanı yükleme bazı bölümleri sonra devam edebilir `AppDomainCreationFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="395bc-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="395bc-111">Bir hata HRESULT içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="395bc-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="395bc-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca ilk bölümü, uygulama etki alanı oluşturma başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="395bc-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="395bc-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="395bc-113">Requirements</span></span>  
 <span data-ttu-id="395bc-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="395bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="395bc-115">**Üst bilgi:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="395bc-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="395bc-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="395bc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="395bc-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="395bc-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="395bc-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="395bc-118">See also</span></span>
- [<span data-ttu-id="395bc-119">ICorProfilerCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="395bc-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
