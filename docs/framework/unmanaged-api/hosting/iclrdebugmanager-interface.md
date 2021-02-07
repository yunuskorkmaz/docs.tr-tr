---
description: ': ICLRDebugManager arabirimi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 4306e38b7c868561276d5b00e7730b6fcee46fd7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746034"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="3b836-103">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3b836-103">ICLRDebugManager Interface</span></span>

<span data-ttu-id="3b836-104">Bir ana bilgisayarın bir dizi görevi bir tanımlayıcıyla ve kolay bir adla ilişkilendirilmesine imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="3b836-104">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3b836-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="3b836-105">Methods</span></span>  
  
|<span data-ttu-id="3b836-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="3b836-106">Method</span></span>|<span data-ttu-id="3b836-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3b836-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3b836-108">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b836-108">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="3b836-109">Görevleri bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="3b836-109">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="3b836-110">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b836-110">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="3b836-111">Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="3b836-111">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="3b836-112">GetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b836-112">GetDacl Method</span></span>](iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="3b836-113">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="3b836-113">This method is not implemented.</span></span>|  
|[<span data-ttu-id="3b836-114">IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b836-114">IsDebuggerAttached Method</span></span>](iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="3b836-115">Bir hata ayıklayıcının işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="3b836-115">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="3b836-116">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b836-116">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="3b836-117">[ICLRTask](iclrtask-interface.md) örneklerinin listesini bir tanımlayıcı ve kolay bir ad ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="3b836-117">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="3b836-118">SetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b836-118">SetDacl Method</span></span>](iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="3b836-119">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="3b836-119">This method is not implemented.</span></span>|  
|[<span data-ttu-id="3b836-120">SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3b836-120">SetSymbolReadingPolicy Method</span></span>](iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="3b836-121">Program veritabanı (PDB) dosyalarını okuma ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="3b836-121">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="3b836-122">İlke, satır numaraları ve dosya hakkındaki bilgilerin çağrı yığınlarına dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="3b836-122">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b836-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3b836-123">Remarks</span></span>  

 <span data-ttu-id="3b836-124">Hata ayıklama senaryolarında, bir ana bilgisayar görevleri kendi programlama mantığına göre gruplamak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="3b836-124">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="3b836-125">Örneğin, bir gruplandırma, bir geliştiricinin işlemde çalışan her görevi görmek yerine yalnızca geliştiricinin API 'Leri için gereken görevleri görmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b836-125">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="3b836-126">`ICLRDebugManager` konağın bu tür gruplamayı uygulamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="3b836-126">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3b836-127">Üç `ICLRDebugManager` Yöntem, `BeginConnection` `SetConnectionTasks` ve birbirlerine `EndConnection` bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="3b836-127">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="3b836-128">Beklenen şekilde çalışması için, bunların belirtilen sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="3b836-128">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="3b836-129">Gruplandırma ve konağın gruplandırmaya atadığı tanımlayıcı ve kolay adlar, ortak dil çalışma zamanı (CLR) için bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="3b836-129">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="3b836-130">CLR, bilgileri yalnızca hata ayıklayıcıyla geçirir.</span><span class="sxs-lookup"><span data-stu-id="3b836-130">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b836-131">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3b836-131">Requirements</span></span>  

 <span data-ttu-id="3b836-132">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b836-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b836-133">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3b836-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3b836-134">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3b836-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3b836-135">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b836-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b836-136">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3b836-136">See also</span></span>

- [<span data-ttu-id="3b836-137">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="3b836-137">Hosting Interfaces</span></span>](hosting-interfaces.md)
