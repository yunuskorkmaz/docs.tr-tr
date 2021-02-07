---
description: 'Daha fazla bilgi edinin: IHostManualEvent:: Reset yöntemi'
title: IHostManualEvent::Reset Yöntemi
ms.date: 03/30/2017
api_name:
- IHostManualEvent.Reset
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostManualEvent::Reset
helpviewer_keywords:
- Reset method, IHostManualEvent interface [.NET Framework hosting]
- IHostManualEvent::Reset method [.NET Framework hosting]
ms.assetid: 0d101168-b5e3-49ce-90c7-85cf2db83c4c
topic_type:
- apiref
ms.openlocfilehash: 84debb8b37c2cdfdbf294bff6736b081424f9e52
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99708079"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="09a8e-103">IHostManualEvent::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="09a8e-103">IHostManualEvent::Reset Method</span></span>

<span data-ttu-id="09a8e-104">Geçerli [IHostManualEvent](ihostmanualevent-interface.md) örneğini, sinyal olmayan bir duruma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="09a8e-104">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09a8e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="09a8e-105">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="09a8e-106">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="09a8e-106">Return Value</span></span>  
  
|<span data-ttu-id="09a8e-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="09a8e-107">HRESULT</span></span>|<span data-ttu-id="09a8e-108">Description</span><span class="sxs-lookup"><span data-stu-id="09a8e-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="09a8e-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="09a8e-109">S_OK</span></span>|<span data-ttu-id="09a8e-110">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="09a8e-110">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="09a8e-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="09a8e-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="09a8e-112">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="09a8e-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="09a8e-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="09a8e-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="09a8e-114">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="09a8e-114">The call timed out.</span></span>|  
|<span data-ttu-id="09a8e-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="09a8e-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="09a8e-116">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="09a8e-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="09a8e-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="09a8e-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="09a8e-118">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="09a8e-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="09a8e-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="09a8e-119">E_FAIL</span></span>|<span data-ttu-id="09a8e-120">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="09a8e-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="09a8e-121">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="09a8e-121">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="09a8e-122">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="09a8e-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="09a8e-123">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="09a8e-123">Requirements</span></span>  

 <span data-ttu-id="09a8e-124">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09a8e-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09a8e-125">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="09a8e-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="09a8e-126">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="09a8e-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="09a8e-127">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09a8e-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09a8e-128">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="09a8e-128">See also</span></span>

- [<span data-ttu-id="09a8e-129">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09a8e-129">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="09a8e-130">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09a8e-130">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="09a8e-131">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09a8e-131">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="09a8e-132">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09a8e-132">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="09a8e-133">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="09a8e-133">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
