---
title: "ICorProfilerCallback::AppDomainCreationFinished Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AppDomainCreationFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AppDomainCreationFinished
helpviewer_keywords:
- AppDomainCreationFinished method [.NET Framework profiling]
- ICorProfilerCallback::AppDomainCreationFinished method [.NET Framework profiling]
ms.assetid: dbab7d90-d515-4dc9-8195-294d5d04bab6
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d21198253e10434b37261d34cf12ef60c26f7e71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackappdomaincreationfinished-method"></a><span data-ttu-id="3ac66-102">ICorProfilerCallback::AppDomainCreationFinished Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3ac66-102">ICorProfilerCallback::AppDomainCreationFinished Method</span></span>
<span data-ttu-id="3ac66-103">Profil Oluşturucu uygulama etki alanı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="3ac66-103">Notifies the profiler that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ac66-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3ac66-104">Syntax</span></span>  
  
```  
HRESULT AppDomainCreationFinished(  
    [in] AppDomainID appDomainId,  
    [in] HRESULT     hrStatus);   
```  
  
#### <a name="parameters"></a><span data-ttu-id="3ac66-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3ac66-105">Parameters</span></span>  
 `appDomainId`  
 <span data-ttu-id="3ac66-106">[in] Oluşturulduktan sonra etki alanı tanımlar.</span><span class="sxs-lookup"><span data-stu-id="3ac66-106">[in] Identifies the domain which has been created.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="3ac66-107">[in] Uygulama etki alanı oluşturulması başarıyla tamamlandı olup olmadığını belirten bir HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3ac66-107">[in] An HRESULT that indicates whether creation of the application domain completed successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ac66-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3ac66-108">Remarks</span></span>  
 <span data-ttu-id="3ac66-109">Uygulama Kimliği kadar herhangi bir bilgi istek için geçerli değil `AppDomainCreationFinished` yöntemi çağrılır.</span><span class="sxs-lookup"><span data-stu-id="3ac66-109">The application ID is not valid for any information request until the `AppDomainCreationFinished` method is called.</span></span>  
  
 <span data-ttu-id="3ac66-110">Uygulama etki alanı yükleme bazı bölümleri sonra devam edebilir `AppDomainCreationFinished` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3ac66-110">Some parts of loading the application domain might continue after the `AppDomainCreationFinished` callback.</span></span> <span data-ttu-id="3ac66-111">HRESULT hata içinde `hrStatus` hata gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ac66-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="3ac66-112">Ancak, bir başarı HRESULT içinde `hrStatus` yalnızca uygulama etki alanı oluşturma ilk bölümü başarılı olduğunu gösterir.</span><span class="sxs-lookup"><span data-stu-id="3ac66-112">However, a success HRESULT in `hrStatus` indicates only that the first part of creating the application domain has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ac66-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3ac66-113">Requirements</span></span>  
 <span data-ttu-id="3ac66-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ac66-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ac66-115">**Başlık:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="3ac66-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3ac66-116">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ac66-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ac66-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ac66-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ac66-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3ac66-118">See Also</span></span>  
 [<span data-ttu-id="3ac66-119">Icorprofilercallback arabirimi</span><span class="sxs-lookup"><span data-stu-id="3ac66-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
