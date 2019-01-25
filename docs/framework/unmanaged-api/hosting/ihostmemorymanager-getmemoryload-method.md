---
title: IHostMemoryManager::GetMemoryLoad Metodu
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18b4ad9590b57b629587af8f421a3f5902e5527f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704036"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="432ff-102">IHostMemoryManager::GetMemoryLoad Metodu</span><span class="sxs-lookup"><span data-stu-id="432ff-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="432ff-103">Şu anda kullanımda ve bu nedenle kullanılamıyor, konak tarafından bildirilen olarak fiziksel bellek miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="432ff-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="432ff-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="432ff-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="432ff-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="432ff-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="432ff-106">[out] Yaklaşık yüzde şu anda kullanılmakta olan toplam fiziksel bellek işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="432ff-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="432ff-107">[out] Ortak dil çalışma zamanı (CLR) kullanılabilir bayt sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="432ff-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="432ff-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="432ff-108">Return Value</span></span>  
  
|<span data-ttu-id="432ff-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="432ff-109">HRESULT</span></span>|<span data-ttu-id="432ff-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="432ff-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="432ff-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="432ff-111">S_OK</span></span>|<span data-ttu-id="432ff-112">`GetMemoryLoad` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="432ff-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="432ff-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="432ff-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="432ff-114">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="432ff-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="432ff-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="432ff-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="432ff-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="432ff-116">The call timed out.</span></span>|  
|<span data-ttu-id="432ff-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="432ff-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="432ff-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="432ff-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="432ff-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="432ff-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="432ff-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="432ff-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="432ff-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="432ff-121">E_FAIL</span></span>|<span data-ttu-id="432ff-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="432ff-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="432ff-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="432ff-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="432ff-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="432ff-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="432ff-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="432ff-125">Remarks</span></span>  
 <span data-ttu-id="432ff-126">`GetMemoryLoad` Win32 sarmalar `GlobalMemoryStatus` işlevi.</span><span class="sxs-lookup"><span data-stu-id="432ff-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="432ff-127">Değerini `pMemoryLoad` eşdeğerdir `dwMemoryLoad` alanındaki `MEMORYSTATUS` döndürüldüğü yapısı `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="432ff-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="432ff-128">Çalışma zamanı, çöp toplayıcının bir buluşsal yöntem dönüş değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="432ff-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="432ff-129">Örneğin, ana bilgisayar bellek çoğunu kullanımda olduğunu bildirirse, çöp toplayıcı potansiyel olarak kullanılabilir hale gelebilir bellek miktarını artırmak için birden çok nesil toplama katılmak bırakmayı.</span><span class="sxs-lookup"><span data-stu-id="432ff-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="432ff-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="432ff-130">Requirements</span></span>  
 <span data-ttu-id="432ff-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="432ff-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="432ff-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="432ff-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="432ff-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="432ff-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="432ff-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="432ff-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="432ff-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="432ff-135">See also</span></span>
- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="432ff-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="432ff-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
