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
ms.openlocfilehash: 90ae790603f0e41a20993ffef88654211a3168d9
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83842367"
---
# <a name="ihosttaskmanagerbeginthreadaffinity-method"></a><span data-ttu-id="aa944-102">IHostTaskManager::BeginThreadAffinity Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aa944-102">IHostTaskManager::BeginThreadAffinity Method</span></span>
<span data-ttu-id="aa944-103">Yönetilen koda, geçerli görevin başka bir işletim sistemi iş parçacığına taşınmaması gereken bir dönem girmediğini bildirir.</span><span class="sxs-lookup"><span data-stu-id="aa944-103">Notifies the host that managed code is entering a period in which the current task must not be moved to another operating system thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa944-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="aa944-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginThreadAffinity ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="aa944-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="aa944-105">Return Value</span></span>  
  
|<span data-ttu-id="aa944-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="aa944-106">HRESULT</span></span>|<span data-ttu-id="aa944-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aa944-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="aa944-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="aa944-108">S_OK</span></span>|<span data-ttu-id="aa944-109">`BeginThreadAffinity`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="aa944-109">`BeginThreadAffinity` returned successfully.</span></span>|  
|<span data-ttu-id="aa944-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="aa944-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="aa944-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="aa944-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="aa944-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="aa944-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="aa944-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="aa944-113">The call timed out.</span></span>|  
|<span data-ttu-id="aa944-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="aa944-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="aa944-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="aa944-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="aa944-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="aa944-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="aa944-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="aa944-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="aa944-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="aa944-118">E_FAIL</span></span>|<span data-ttu-id="aa944-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="aa944-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="aa944-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="aa944-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="aa944-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="aa944-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa944-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="aa944-122">Remarks</span></span>  
 <span data-ttu-id="aa944-123">CLR genellikle `IHostTaskManager::BeginThreadAffinity` çağrısı bağlamında çağırır <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="aa944-123">The CLR typically calls `IHostTaskManager::BeginThreadAffinity` in the context of a call to <xref:System.Threading.Thread.BeginThreadAffinity%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="aa944-124">[IHostTaskManager:: Endthreayıffinity](ihosttaskmanager-endthreadaffinity-method.md)öğesine karşılık gelen bir çağrı yapılıncaya kadar geçerli görevin yeniden zamanlanmamalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa944-124">The current task must not be rescheduled until a corresponding call is made to [IHostTaskManager::EndThreadAffinity](ihosttaskmanager-endthreadaffinity-method.md).</span></span> <span data-ttu-id="aa944-125">Görevler dışarı değiştirilebilir, ancak geri yüklendiğinde, bunların dışarı geçirildiği işletim sistemi iş parçacığına atanması gerekir. `BeginThreadAffinity`Çağrı geçerli göreve başvurduğundan, iç içe çağrılar hiçbir etkiye sahip değildir.</span><span class="sxs-lookup"><span data-stu-id="aa944-125">Tasks can be switched out, but when they are switched back in, they must be assigned to the same operating system thread from which they were switched out. Nested calls to `BeginThreadAffinity` have no effect, because the call refers to the current task.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa944-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aa944-126">Requirements</span></span>  
 <span data-ttu-id="aa944-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa944-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa944-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aa944-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aa944-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="aa944-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aa944-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa944-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa944-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa944-131">See also</span></span>

- [<span data-ttu-id="aa944-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa944-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="aa944-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa944-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="aa944-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa944-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="aa944-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aa944-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
