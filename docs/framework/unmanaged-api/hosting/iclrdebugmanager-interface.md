---
title: ICLRDebugManager Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 22c3a480e2b68377e300df1083b3178ee4e2d2a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61969864"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="6336b-102">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6336b-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="6336b-103">Bir görev kümesi bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek konak izin vermek için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6336b-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6336b-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="6336b-104">Methods</span></span>  
  
|<span data-ttu-id="6336b-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="6336b-105">Method</span></span>|<span data-ttu-id="6336b-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6336b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6336b-107">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6336b-107">BeginConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="6336b-108">Konak ve hata ayıklayıcı görevleri bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="6336b-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="6336b-109">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6336b-109">EndConnection Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="6336b-110">Görevlerin bir listesi ve tanımlayıcı bir kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="6336b-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="6336b-111">GetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6336b-111">GetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="6336b-112">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6336b-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="6336b-113">IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6336b-113">IsDebuggerAttached Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="6336b-114">Bir hata ayıklayıcı işleme ekli olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="6336b-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="6336b-115">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6336b-115">SetConnectionTasks Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="6336b-116">Listesini ilişkilendirir [Iclrtask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) örnekleriyle tanımlayıcı ve bir kolay ad.</span><span class="sxs-lookup"><span data-stu-id="6336b-116">Associates a list of [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="6336b-117">SetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6336b-117">SetDacl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="6336b-118">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="6336b-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="6336b-119">SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6336b-119">SetSymbolReadingPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="6336b-120">Program veritabanı (PDB) dosyaları okumak için ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="6336b-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="6336b-121">İlke satır numaraları ve dosyaları hakkında bilgi çağrı yığınlarıyla içerilip içerilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="6336b-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6336b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6336b-122">Remarks</span></span>  
 <span data-ttu-id="6336b-123">Hata ayıklama senaryoları bir konak grubu görevleri programlama mantığını göre isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="6336b-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="6336b-124">Örneğin, bir gruplandırma bir geliştirici Geliştirici API'leri, işlemde çalışan her görev görmek yerine gerektirdiği görevleri görmek izin verir.</span><span class="sxs-lookup"><span data-stu-id="6336b-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="6336b-125">`ICLRDebugManager` Bu tür bir gruplandırma uygulamak konak sağlar.</span><span class="sxs-lookup"><span data-stu-id="6336b-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="6336b-126">Üç `ICLRDebugManager` yöntemleri `BeginConnection`, `SetConnectionTasks` ve `EndConnection`, birbirine bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="6336b-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="6336b-127">Verildikleri sırada beklendiği şekilde çalışması için çağrılmalıdır.</span><span class="sxs-lookup"><span data-stu-id="6336b-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="6336b-128">Gruplandırma ve tanımlayıcıları ve konak gruba atar. kolay adlar bir ortak dil çalışma zamanı (CLR) için hiçbir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="6336b-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="6336b-129">CLR, yalnızca hata ayıklayıcıyı boyunca bilgileri geçirir.</span><span class="sxs-lookup"><span data-stu-id="6336b-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6336b-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6336b-130">Requirements</span></span>  
 <span data-ttu-id="6336b-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6336b-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6336b-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6336b-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6336b-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6336b-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6336b-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6336b-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6336b-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6336b-135">See also</span></span>

- [<span data-ttu-id="6336b-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="6336b-136">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
