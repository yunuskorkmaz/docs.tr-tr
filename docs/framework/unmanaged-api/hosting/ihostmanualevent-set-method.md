---
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
ms.openlocfilehash: b5cd02f54a930942e1892f88fb3d8e926a6f3e1b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83804566"
---
# <a name="ihostmanualeventset-method"></a><span data-ttu-id="36510-102">IHostManualEvent::Set Yöntemi</span><span class="sxs-lookup"><span data-stu-id="36510-102">IHostManualEvent::Set Method</span></span>
<span data-ttu-id="36510-103">Geçerli [IHostManualEvent](ihostmanualevent-interface.md) örneğini sinyal verilmiş bir duruma ayarlar.</span><span class="sxs-lookup"><span data-stu-id="36510-103">Sets the current [IHostManualEvent](ihostmanualevent-interface.md) instance to a signaled state.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36510-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="36510-104">Syntax</span></span>  
  
```cpp  
HRESULT Set ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="36510-105">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36510-105">Return Value</span></span>  
  
|<span data-ttu-id="36510-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36510-106">HRESULT</span></span>|<span data-ttu-id="36510-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36510-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36510-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="36510-108">S_OK</span></span>|<span data-ttu-id="36510-109">`Set`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="36510-109">`Set` returned successfully.</span></span>|  
|<span data-ttu-id="36510-110">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36510-110">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36510-111">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="36510-111">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36510-112">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36510-112">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36510-113">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="36510-113">The call timed out.</span></span>|  
|<span data-ttu-id="36510-114">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36510-114">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36510-115">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="36510-115">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36510-116">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36510-116">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36510-117">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="36510-117">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36510-118">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="36510-118">E_FAIL</span></span>|<span data-ttu-id="36510-119">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="36510-119">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36510-120">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="36510-120">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36510-121">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="36510-121">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="36510-122">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36510-122">Requirements</span></span>  
 <span data-ttu-id="36510-123">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36510-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36510-124">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="36510-124">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36510-125">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="36510-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36510-126">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36510-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36510-127">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36510-127">See also</span></span>

- [<span data-ttu-id="36510-128">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36510-128">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="36510-129">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36510-129">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="36510-130">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36510-130">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="36510-131">IHostSemaphore Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36510-131">IHostSemaphore Interface</span></span>](ihostsemaphore-interface.md)
- [<span data-ttu-id="36510-132">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36510-132">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
