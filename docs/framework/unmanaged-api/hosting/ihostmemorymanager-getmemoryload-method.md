---
title: IHostMemoryManager::GetMemoryLoad Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 320881447eed00bf0dfeada0f5fbd224c32dfe96
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="149e5-102">IHostMemoryManager::GetMemoryLoad Metodu</span><span class="sxs-lookup"><span data-stu-id="149e5-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="149e5-103">Şu anda kullanımda ve bu nedenle kullanılamaz, ana bilgisayar tarafından bildirilen olarak fiziksel bellek miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="149e5-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="149e5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="149e5-104">Syntax</span></span>  
  
```  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="149e5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="149e5-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="149e5-106">[out] Şu anda kullanımda toplam fiziksel bellek yaklaşık yüzdesi için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="149e5-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="149e5-107">[out] Ortak dil çalışma zamanı (CLR) kullanılabilir bayt sayısını gösteren bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="149e5-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="149e5-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="149e5-108">Return Value</span></span>  
  
|<span data-ttu-id="149e5-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="149e5-109">HRESULT</span></span>|<span data-ttu-id="149e5-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="149e5-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="149e5-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="149e5-111">S_OK</span></span>|<span data-ttu-id="149e5-112">`GetMemoryLoad`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="149e5-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="149e5-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="149e5-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="149e5-114">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="149e5-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="149e5-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="149e5-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="149e5-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="149e5-116">The call timed out.</span></span>|  
|<span data-ttu-id="149e5-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="149e5-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="149e5-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="149e5-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="149e5-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="149e5-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="149e5-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="149e5-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="149e5-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="149e5-121">E_FAIL</span></span>|<span data-ttu-id="149e5-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="149e5-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="149e5-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="149e5-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="149e5-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="149e5-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="149e5-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="149e5-125">Remarks</span></span>  
 <span data-ttu-id="149e5-126">`GetMemoryLoad`Win32 sarmalar `GlobalMemoryStatus` işlevi.</span><span class="sxs-lookup"><span data-stu-id="149e5-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="149e5-127">Değeri `pMemoryLoad` eşdeğerdir `dwMemoryLoad` alanındaki `MEMORYSTATUS` döndürülen yapısı `GlobalMemoryStatus`.</span><span class="sxs-lookup"><span data-stu-id="149e5-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="149e5-128">Çalışma zamanı dönüş değeri için atık toplayıcısını buluşsal yöntem kullanır.</span><span class="sxs-lookup"><span data-stu-id="149e5-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="149e5-129">Örneğin, ana bilgisayarın bellek çoğunluğu kullanımda olduğunu bildirirse, potansiyel olarak kullanılabilir hale gelebilir bellek miktarını artırmak için birden çok nesli toplamak atık toplayıcı tercih edebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="149e5-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="149e5-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="149e5-130">Requirements</span></span>  
 <span data-ttu-id="149e5-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="149e5-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="149e5-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="149e5-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="149e5-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="149e5-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="149e5-134">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="149e5-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="149e5-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="149e5-135">See Also</span></span>  
 <xref:System.GC?displayProperty=nameWithType>  
 [<span data-ttu-id="149e5-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="149e5-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
