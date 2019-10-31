---
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
ms.openlocfilehash: 7c157cf27d2fe86288024a6c35e6dcbea3c46347
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133116"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="a57ff-102">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a57ff-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="a57ff-103">Yönetilen koda, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken bir dönem girmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="a57ff-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a57ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a57ff-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="a57ff-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a57ff-105">Return Value</span></span>  
  
|<span data-ttu-id="a57ff-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a57ff-106">HRESULT</span></span>|<span data-ttu-id="a57ff-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a57ff-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a57ff-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="a57ff-108">S_OK</span></span>|<span data-ttu-id="a57ff-109">`BeginThreadAffinity` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a57ff-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="a57ff-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a57ff-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a57ff-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="a57ff-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a57ff-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a57ff-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a57ff-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a57ff-113">The call timed out.</span></span>|  
|<span data-ttu-id="a57ff-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a57ff-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a57ff-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="a57ff-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a57ff-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a57ff-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a57ff-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="a57ff-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a57ff-118">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="a57ff-118">E_FAIL</span></span>|<span data-ttu-id="a57ff-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a57ff-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a57ff-120">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a57ff-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a57ff-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a57ff-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a57ff-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a57ff-122">Remarks</span></span>  
 <span data-ttu-id="a57ff-123">CLR genellikle <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>çağrısı bağlamında `IHostTaskManager::BeginThreadAffinity` çağırır.</span><span class="sxs-lookup"><span data-stu-id="a57ff-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="a57ff-124">[IHostTaskManager:: Endthreayıffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md)öğesine karşılık gelen bir çağrı yapılıncaya kadar geçerli görevin yeniden zamanlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="a57ff-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="a57ff-125">Görevler dışarı değiştirilebilir, ancak geri yüklendiğinde, bunların dışarı geçirildiği işletim sistemi iş parçacığına atanması gerekir. Çağrı geçerli göreve başvurduğundan `BeginThreadAffinity` iç içe çağrılar hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="a57ff-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a57ff-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a57ff-126">Requirements</span></span>  
 <span data-ttu-id="a57ff-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a57ff-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a57ff-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a57ff-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a57ff-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="a57ff-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a57ff-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a57ff-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a57ff-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a57ff-131">See also</span></span>

- [<span data-ttu-id="a57ff-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a57ff-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="a57ff-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a57ff-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="a57ff-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a57ff-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="a57ff-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a57ff-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
