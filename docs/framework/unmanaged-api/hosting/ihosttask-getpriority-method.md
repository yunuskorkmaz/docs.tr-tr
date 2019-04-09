---
title: IHostTask::GetPriority Metodu
ms.date: 03/30/2017
api_name:
- IHostTask.GetPriority
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTask::GetPriority
helpviewer_keywords:
- GetPriority method [.NET Framework hosting]
- IHostTask::GetPriority method [.NET Framework hosting]
ms.assetid: 4b463cd6-77c1-4f9a-8518-346ad8fc4b70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 702992ab4edfea3f0b699efefedb195cd87586ea
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136779"
---
# <a name="ihosttaskgetpriority-method"></a><span data-ttu-id="c1a98-102">IHostTask::GetPriority Metodu</span><span class="sxs-lookup"><span data-stu-id="c1a98-102">IHostTask::GetPriority Method</span></span>
<span data-ttu-id="c1a98-103">İş parçacığı öncelik düzeyi geçerli tarafından temsil edilen bir görev alır [Ihosttask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="c1a98-103">Gets the thread priority level of the task represented by the current [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1a98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c1a98-104">Syntax</span></span>  
  
```  
HRESULT GetPriority (  
    [out] int *pPriority  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1a98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1a98-105">Parameters</span></span>  
 `pPriority`  
 <span data-ttu-id="c1a98-106">[out] Geçerli tarafından temsil edilen bir görev iş parçacığı öncelik düzeyi belirten bir tamsayı işaretçisi `IHostTask` örneği.</span><span class="sxs-lookup"><span data-stu-id="c1a98-106">[out] A pointer to an integer that indicates the thread priority level of the task represented by the current `IHostTask` instance.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1a98-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1a98-107">Return Value</span></span>  
  
|<span data-ttu-id="c1a98-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1a98-108">HRESULT</span></span>|<span data-ttu-id="c1a98-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1a98-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1a98-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1a98-110">S_OK</span></span>|`GetPriority` <span data-ttu-id="c1a98-111">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c1a98-111">returned successfully.</span></span>|  
|<span data-ttu-id="c1a98-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1a98-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1a98-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="c1a98-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c1a98-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c1a98-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c1a98-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c1a98-115">The call timed out.</span></span>|  
|<span data-ttu-id="c1a98-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c1a98-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c1a98-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c1a98-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c1a98-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c1a98-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c1a98-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="c1a98-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c1a98-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1a98-120">E_FAIL</span></span>|<span data-ttu-id="c1a98-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c1a98-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c1a98-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c1a98-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c1a98-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1a98-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1a98-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1a98-124">Remarks</span></span>  
 <span data-ttu-id="c1a98-125">Win32 iş parçacığı öncelik düzeyi değerleri tanımlanmış `SetThreadPriority` işlevi.</span><span class="sxs-lookup"><span data-stu-id="c1a98-125">Thread priority level values are defined by the Win32 `SetThreadPriority` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1a98-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1a98-126">Requirements</span></span>  
 <span data-ttu-id="c1a98-127">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1a98-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1a98-128">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c1a98-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1a98-129">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c1a98-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c1a98-130">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c1a98-130">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c1a98-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1a98-131">See also</span></span>

- [<span data-ttu-id="c1a98-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a98-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="c1a98-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a98-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="c1a98-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a98-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="c1a98-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1a98-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
