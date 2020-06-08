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
ms.openlocfilehash: 653c8d1d3edd38e646b4e90c0e48dbe15bed102a
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504270"
---
# <a name="iclrdebugmanager-interface"></a><span data-ttu-id="40dd3-102">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="40dd3-102">ICLRDebugManager Interface</span></span>
<span data-ttu-id="40dd3-103">Bir ana bilgisayarın bir dizi görevi bir tanımlayıcıyla ve kolay bir adla ilişkilendirilmesine imkan tanıyan yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="40dd3-103">Provides methods that allow a host to associate a set of tasks with an identifier and a friendly name.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40dd3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="40dd3-104">Methods</span></span>  
  
|<span data-ttu-id="40dd3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="40dd3-105">Method</span></span>|<span data-ttu-id="40dd3-106">Description</span><span class="sxs-lookup"><span data-stu-id="40dd3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40dd3-107">BeginConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40dd3-107">BeginConnection Method</span></span>](iclrdebugmanager-beginconnection-method.md)|<span data-ttu-id="40dd3-108">Görevleri bir tanımlayıcı ve kolay bir ad ile ilişkilendirmek için ana bilgisayar ile hata ayıklayıcı arasında yeni bir bağlantı kurar.</span><span class="sxs-lookup"><span data-stu-id="40dd3-108">Establishes a new connection between the host and the debugger to associate tasks with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="40dd3-109">EndConnection Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40dd3-109">EndConnection Method</span></span>](iclrdebugmanager-endconnection-method.md)|<span data-ttu-id="40dd3-110">Bir görev listesi ve tanımlayıcı ve kolay ad arasındaki ilişkiyi kaldırır.</span><span class="sxs-lookup"><span data-stu-id="40dd3-110">Removes the association between a list of tasks and an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="40dd3-111">GetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40dd3-111">GetDacl Method</span></span>](iclrdebugmanager-getdacl-method.md)|<span data-ttu-id="40dd3-112">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="40dd3-112">This method is not implemented.</span></span>|  
|[<span data-ttu-id="40dd3-113">IsDebuggerAttached Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40dd3-113">IsDebuggerAttached Method</span></span>](iclrdebugmanager-isdebuggerattached-method.md)|<span data-ttu-id="40dd3-114">Bir hata ayıklayıcının işleme bağlı olup olmadığını gösteren bir değer alır.</span><span class="sxs-lookup"><span data-stu-id="40dd3-114">Gets a value that indicates whether a debugger is attached to the process.</span></span>|  
|[<span data-ttu-id="40dd3-115">SetConnectionTasks Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40dd3-115">SetConnectionTasks Method</span></span>](iclrdebugmanager-setconnectiontasks-method.md)|<span data-ttu-id="40dd3-116">[ICLRTask](iclrtask-interface.md) örneklerinin listesini bir tanımlayıcı ve kolay bir ad ile ilişkilendirir.</span><span class="sxs-lookup"><span data-stu-id="40dd3-116">Associates a list of [ICLRTask](iclrtask-interface.md) instances with an identifier and a friendly name.</span></span>|  
|[<span data-ttu-id="40dd3-117">SetDacl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40dd3-117">SetDacl Method</span></span>](iclrdebugmanager-setdacl-method.md)|<span data-ttu-id="40dd3-118">Bu yöntem uygulanmadı.</span><span class="sxs-lookup"><span data-stu-id="40dd3-118">This method is not implemented.</span></span>|  
|[<span data-ttu-id="40dd3-119">SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="40dd3-119">SetSymbolReadingPolicy Method</span></span>](iclrdebugmanager-setsymbolreadingpolicy-method.md)|<span data-ttu-id="40dd3-120">Program veritabanı (PDB) dosyalarını okuma ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="40dd3-120">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="40dd3-121">İlke, satır numaraları ve dosya hakkındaki bilgilerin çağrı yığınlarına dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="40dd3-121">The policy determines whether information about line numbers and files is included in call stacks.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40dd3-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="40dd3-122">Remarks</span></span>  
 <span data-ttu-id="40dd3-123">Hata ayıklama senaryolarında, bir ana bilgisayar görevleri kendi programlama mantığına göre gruplamak isteyebilir.</span><span class="sxs-lookup"><span data-stu-id="40dd3-123">In debugging scenarios, a host might want to group tasks according to its own programming logic.</span></span> <span data-ttu-id="40dd3-124">Örneğin, bir gruplandırma, bir geliştiricinin işlemde çalışan her görevi görmek yerine yalnızca geliştiricinin API 'Leri için gereken görevleri görmesine izin verir.</span><span class="sxs-lookup"><span data-stu-id="40dd3-124">For example, a grouping would allow a developer to see only the tasks required by the developer's APIs, instead of seeing every task running in the process.</span></span> <span data-ttu-id="40dd3-125">`ICLRDebugManager`konağın bu tür gruplamayı uygulamasına izin verir.</span><span class="sxs-lookup"><span data-stu-id="40dd3-125">`ICLRDebugManager` allows the host to implement this kind of grouping.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="40dd3-126">Üç `ICLRDebugManager` Yöntem, `BeginConnection` `SetConnectionTasks` ve birbirlerine `EndConnection` bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="40dd3-126">Three `ICLRDebugManager` methods, `BeginConnection`, `SetConnectionTasks` and `EndConnection`, are dependent upon each other.</span></span> <span data-ttu-id="40dd3-127">Beklenen şekilde çalışması için, bunların belirtilen sırada çağrılması gerekir.</span><span class="sxs-lookup"><span data-stu-id="40dd3-127">They must be called in the given order to work as expected.</span></span>  
  
 <span data-ttu-id="40dd3-128">Gruplandırma ve konağın gruplandırmaya atadığı tanımlayıcı ve kolay adlar, ortak dil çalışma zamanı (CLR) için bir anlamı yoktur.</span><span class="sxs-lookup"><span data-stu-id="40dd3-128">The grouping, and the identifiers and friendly names that the host assigns to the grouping, have no meaning for the common language runtime (CLR).</span></span> <span data-ttu-id="40dd3-129">CLR, bilgileri yalnızca hata ayıklayıcıyla geçirir.</span><span class="sxs-lookup"><span data-stu-id="40dd3-129">The CLR merely passes the information along to the debugger.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40dd3-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="40dd3-130">Requirements</span></span>  
 <span data-ttu-id="40dd3-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40dd3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40dd3-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="40dd3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40dd3-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="40dd3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="40dd3-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40dd3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40dd3-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="40dd3-135">See also</span></span>

- [<span data-ttu-id="40dd3-136">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="40dd3-136">Hosting Interfaces</span></span>](hosting-interfaces.md)
