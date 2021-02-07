---
description: 'Daha fazla bilgi edinin: IHostManualEvent:: set yöntemi'
title: IHostManualEvent::Set Yöntemi
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Set
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Set
helpviewer_keywords:
- Set method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Set method [.NET Framework hosting]
ms.assetid: e930c174-f71d-4faa-bb59-f0fb3df4d77b
topic_type:
- apiref
ms.openlocfilehash: e2de1fde2f8c0f512733ecde43d5240a94f84264
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707936"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="1bc09-103">IHostManualEvent::Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1bc09-103">IHostManualEvent::Set Method</span></span>

<span data-ttu-id="1bc09-104">Geçerli [IHostManualEvent](ihostmanualevent-interface.md) örneğini sinyal verilmiş bir duruma ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1bc09-104">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bc09-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1bc09-105">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1bc09-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="1bc09-106">Return Value</span></span>  
  
|<span data-ttu-id="1bc09-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1bc09-107">HRESULT</span></span>|<span data-ttu-id="1bc09-108">Description</span><span class="sxs-lookup"><span data-stu-id="1bc09-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1bc09-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="1bc09-109">S_OK</span></span>|<span data-ttu-id="1bc09-110">`Set` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="1bc09-110">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="1bc09-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1bc09-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1bc09-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="1bc09-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1bc09-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1bc09-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1bc09-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="1bc09-114">The call timed out.</span></span>|  
|<span data-ttu-id="1bc09-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1bc09-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1bc09-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="1bc09-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1bc09-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1bc09-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1bc09-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="1bc09-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1bc09-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1bc09-119">E_FAIL</span></span>|<span data-ttu-id="1bc09-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="1bc09-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1bc09-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="1bc09-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1bc09-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="1bc09-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1bc09-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1bc09-123">Requirements</span></span>  

 <span data-ttu-id="1bc09-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bc09-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bc09-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1bc09-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1bc09-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="1bc09-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1bc09-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bc09-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bc09-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="1bc09-128">See also</span></span>

- [<span data-ttu-id="1bc09-129">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bc09-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="1bc09-130">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bc09-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="1bc09-131">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bc09-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="1bc09-132">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bc09-132">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="1bc09-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1bc09-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
