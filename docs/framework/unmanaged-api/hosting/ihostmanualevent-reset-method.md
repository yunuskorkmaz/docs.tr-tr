---
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
ms.openlocfilehash: 5653f874ef7a681f6667b3508b82ac493234cc4e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673156"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="2e18e-102">IHostManualEvent::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2e18e-102">IHostManualEvent::Reset Method</span></span>

<span data-ttu-id="2e18e-103">Geçerli [IHostManualEvent](ihostmanualevent-interface.md) örneğini, sinyal olmayan bir duruma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="2e18e-103">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e18e-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="2e18e-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2e18e-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2e18e-105">Return Value</span></span>  
  
|<span data-ttu-id="2e18e-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2e18e-106">HRESULT</span></span>|<span data-ttu-id="2e18e-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2e18e-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2e18e-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="2e18e-108">S_OK</span></span>|<span data-ttu-id="2e18e-109">`Reset` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2e18e-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="2e18e-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2e18e-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2e18e-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2e18e-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2e18e-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2e18e-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2e18e-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2e18e-113">The call timed out.</span></span>|  
|<span data-ttu-id="2e18e-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2e18e-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2e18e-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="2e18e-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2e18e-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2e18e-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2e18e-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="2e18e-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2e18e-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2e18e-118">E_FAIL</span></span>|<span data-ttu-id="2e18e-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2e18e-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2e18e-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2e18e-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2e18e-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2e18e-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e18e-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2e18e-122">Requirements</span></span>  

 <span data-ttu-id="2e18e-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e18e-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e18e-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e18e-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e18e-125">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2e18e-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e18e-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e18e-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e18e-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2e18e-127">See also</span></span>

- [<span data-ttu-id="2e18e-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e18e-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="2e18e-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e18e-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="2e18e-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e18e-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="2e18e-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e18e-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="2e18e-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2e18e-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
