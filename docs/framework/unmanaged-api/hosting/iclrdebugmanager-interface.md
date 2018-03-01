---
title: ICLRDebugManager Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRDebugManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager
helpviewer_keywords:
- ICLRDebugManager interface [.NET Framework hosting]
ms.assetid: e835062c-c7d6-4945-8a44-2de7ebf3928e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8e712f22156e96cfc58e9c1a835077ba21ecd184
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="feb2d-102">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="feb2d-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="feb2d-103">Bir dizi görevi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek konak izin vermek yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="feb2d-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="feb2d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="feb2d-104">Methods</span></span>  
  
|<span data-ttu-id="feb2d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="feb2d-105">Method</span></span>|<span data-ttu-id="feb2d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="feb2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="feb2d-107">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb2d-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="feb2d-108">Ana bilgisayar ve hata ayıklayıcısı görevleri bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="feb2d-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="feb2d-109">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb2d-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="feb2d-110">Görevlerin bir listesi ve bir tanımlayıcı ve bir kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="feb2d-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="feb2d-111">GetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb2d-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="feb2d-112">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="feb2d-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="feb2d-113">IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb2d-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="feb2d-114">İşleme bir hata ayıklayıcısı ekli olup olmadığını belirten bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="feb2d-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="feb2d-115">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb2d-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="feb2d-116">Listesini ilişkilendirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) tanımlayıcı ve kolay bir ad ile örnekleri.</span><span class="sxs-lookup"><span data-stu-id="feb2d-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="feb2d-117">SetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb2d-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="feb2d-118">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="feb2d-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="feb2d-119">SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="feb2d-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="feb2d-120">Program veritabanı (PDB) dosyaları okumak için ilke ayarlar.</span><span class="sxs-lookup"><span data-stu-id="feb2d-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="feb2d-121">İlke çağrı yığınları satır numaralarını ve dosyalarla ilgili bilgiler dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="feb2d-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="feb2d-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="feb2d-122">Remarks</span></span>  
 <span data-ttu-id="feb2d-123">Senaryoları hata ayıklama, bir konak grubu görevleri programlama mantığındaki göre isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="feb2d-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="feb2d-124">Örneğin, bir gruplandırma işleminde çalışan her görev görmesini yerine Geliştirici API'leri, gerekli görevleri görmek bir geliştirici olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="feb2d-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="feb2d-125">`ICLRDebugManager`Bu tür bir gruplandırma uygulamak için ana sağlar.</span><span class="sxs-lookup"><span data-stu-id="feb2d-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="feb2d-126">Üç `ICLRDebugManager` yöntemleri `BeginConnection`, `SetConnectionTasks` ve `EndConnection`, birbirine bağımlıdır.</span><span class="sxs-lookup"><span data-stu-id="feb2d-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="feb2d-127">Beklendiği şekilde çalışması için verildikleri sırada çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="feb2d-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="feb2d-128">Gruplandırma ve tanımlayıcıları ve gruplandırma için konak atar kolay adlar ortak dil çalışma zamanı (CLR) için hiçbir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="feb2d-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="feb2d-129">CLR boyunca bilgi için hata ayıklayıcı yalnızca geçirir.</span><span class="sxs-lookup"><span data-stu-id="feb2d-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="feb2d-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="feb2d-130">Requirements</span></span>  
 <span data-ttu-id="feb2d-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="feb2d-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="feb2d-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="feb2d-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="feb2d-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="feb2d-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="feb2d-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="feb2d-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="feb2d-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="feb2d-135">See Also</span></span>  
 [<span data-ttu-id="feb2d-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="feb2d-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
