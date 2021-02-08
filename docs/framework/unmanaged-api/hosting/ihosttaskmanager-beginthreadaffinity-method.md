---
description: 'Şu konuda daha fazla bilgi edinin: IHostTaskManager:: Beginthreadadffinity yöntemi'
title: IHostTaskManager::BeginThreadAffinity Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.BeginThreadAffinity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::BeginThreadAffinity
helpviewer_keywords:
- IHostTaskManager::BeginThreadAffinity method [.NET Framework hosting]
- BeginThreadAffinity method [.NET Framework hosting]
ms.assetid: fea3ab88-ce41-4c5a-847b-bb78cd748da6
topic_type:
- apiref
ms.openlocfilehash: 15ee917f5c81ee605c0cb4df3180041797c18daf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784606"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="5de29-103">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5de29-103">IHostTaskManager::BeginThreadAffinity Method</span></span>

<span data-ttu-id="5de29-104">Yönetilen koda, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken bir dönem girmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="5de29-104">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5de29-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5de29-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="5de29-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5de29-106">Return Value</span></span>  
  
|<span data-ttu-id="5de29-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5de29-107">HRESULT</span></span>|<span data-ttu-id="5de29-108">Description</span><span class="sxs-lookup"><span data-stu-id="5de29-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5de29-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="5de29-109">S_OK</span></span>|<span data-ttu-id="5de29-110">`BeginThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="5de29-110">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="5de29-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5de29-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5de29-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5de29-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="5de29-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="5de29-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="5de29-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="5de29-114">The call timed out.</span></span>|  
|<span data-ttu-id="5de29-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="5de29-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="5de29-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="5de29-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="5de29-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="5de29-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="5de29-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="5de29-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="5de29-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5de29-119">E_FAIL</span></span>|<span data-ttu-id="5de29-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5de29-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="5de29-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5de29-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="5de29-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5de29-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5de29-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5de29-123">Remarks</span></span>  

 <span data-ttu-id="5de29-124">CLR genellikle `IHostTaskManager::BeginThreadAffinity` çağrısı bağlamında çağırır <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5de29-124">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5de29-125">[IHostTaskManager:: Endthreayıffinity](ihosttaskmanager-endthreadaffinity-method.md)öğesine karşılık gelen bir çağrı yapılıncaya kadar geçerli görevin yeniden zamanlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="5de29-125">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="5de29-126">Görevler dışarı değiştirilebilir, ancak geri yüklendiğinde, bunların dışarı geçirildiği işletim sistemi iş parçacığına atanması gerekir. `BeginThreadAffinity` Çağrı geçerli göreve başvurduğundan, iç içe çağrılar hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="5de29-126">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5de29-127">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5de29-127">Requirements</span></span>  

 <span data-ttu-id="5de29-128">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5de29-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5de29-129">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5de29-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5de29-130">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5de29-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5de29-131">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5de29-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5de29-132">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5de29-132">See also</span></span>

- [<span data-ttu-id="5de29-133">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5de29-133">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="5de29-134">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5de29-134">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="5de29-135">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5de29-135">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="5de29-136">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5de29-136">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
