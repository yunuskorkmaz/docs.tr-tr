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
ms.openlocfilehash: 049a0ae6d860c7c431d08af8ba4539656b8e5592
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804580"
---
# <a name="ihostmanualeventreset-method"></a><span data-ttu-id="309be-102">IHostManualEvent::Reset Yöntemi</span><span class="sxs-lookup"><span data-stu-id="309be-102">IHostManualEvent::Reset Method</span></span>
<span data-ttu-id="309be-103">Geçerli [IHostManualEvent](ihostmanualevent-interface.md) örneğini, sinyal olmayan bir duruma sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="309be-103">Resets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a non-signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="309be-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="309be-104">Syntax</span></span>  
  
```cpp  
HRESULT Reset ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="309be-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="309be-105">Return Value</span></span>  
  
|<span data-ttu-id="309be-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="309be-106">HRESULT</span></span>|<span data-ttu-id="309be-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="309be-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="309be-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="309be-108">S_OK</span></span>|<span data-ttu-id="309be-109">`Reset`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="309be-109">`Reset` returned successfully.</span></span>|  
|<span data-ttu-id="309be-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="309be-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="309be-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="309be-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="309be-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="309be-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="309be-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="309be-113">The call timed out.</span></span>|  
|<span data-ttu-id="309be-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="309be-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="309be-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="309be-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="309be-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="309be-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="309be-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="309be-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="309be-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="309be-118">E_FAIL</span></span>|<span data-ttu-id="309be-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="309be-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="309be-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="309be-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="309be-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="309be-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="309be-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="309be-122">Requirements</span></span>  
 <span data-ttu-id="309be-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="309be-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="309be-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="309be-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="309be-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="309be-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="309be-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="309be-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="309be-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="309be-127">See also</span></span>

- [<span data-ttu-id="309be-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="309be-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="309be-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="309be-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="309be-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="309be-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="309be-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="309be-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="309be-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="309be-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
