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
ms.openlocfilehash: 88acd50c83eb1ff4d59aa50d677db2383912659a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176285"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="01f76-102">IHostMemoryManager::GetMemoryLoad Metodu</span><span class="sxs-lookup"><span data-stu-id="01f76-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="01f76-103">Ana bilgisayar tarafından bildirilen, şu anda kullanılmakta olan ve bu nedenle kullanılamayan fiziksel bellek miktarını alır.</span><span class="sxs-lookup"><span data-stu-id="01f76-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01f76-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="01f76-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01f76-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="01f76-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="01f76-106">[çıkış] Şu anda kullanılmakta olan toplam fiziksel belleğin yaklaşık yüzdesine işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01f76-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="01f76-107">[çıkış] Ortak dil çalışma zamanı (CLR) için kullanılabilir bayt sayısıiçin bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="01f76-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01f76-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="01f76-108">Return Value</span></span>  
  
|<span data-ttu-id="01f76-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="01f76-109">HRESULT</span></span>|<span data-ttu-id="01f76-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="01f76-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="01f76-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="01f76-111">S_OK</span></span>|<span data-ttu-id="01f76-112">`GetMemoryLoad`başarıyla döndürülür.</span><span class="sxs-lookup"><span data-stu-id="01f76-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="01f76-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="01f76-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="01f76-114">CLR bir işleme yüklenmedi veya CLR yönetilen kodu çalıştıramadığı veya aramayı başarıyla işleyemediği bir durumdadır.</span><span class="sxs-lookup"><span data-stu-id="01f76-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="01f76-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="01f76-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="01f76-116">Arama zaman doldu.</span><span class="sxs-lookup"><span data-stu-id="01f76-116">The call timed out.</span></span>|  
|<span data-ttu-id="01f76-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="01f76-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="01f76-118">Arayan kilidin sahibi değildir.</span><span class="sxs-lookup"><span data-stu-id="01f76-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="01f76-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="01f76-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="01f76-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="01f76-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="01f76-121">E_faıl</span><span class="sxs-lookup"><span data-stu-id="01f76-121">E_FAIL</span></span>|<span data-ttu-id="01f76-122">Bilinmeyen bir felaket hatası meydana geldi.</span><span class="sxs-lookup"><span data-stu-id="01f76-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="01f76-123">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="01f76-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="01f76-124">Barındırma yöntemleri sonraki aramalar HOST_E_CLRNOTAVAILABLE döndürün.</span><span class="sxs-lookup"><span data-stu-id="01f76-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01f76-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="01f76-125">Remarks</span></span>  
 <span data-ttu-id="01f76-126">`GetMemoryLoad`Win32 `GlobalMemoryStatus` işlevini sarar.</span><span class="sxs-lookup"><span data-stu-id="01f76-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="01f76-127">Değeri, `pMemoryLoad` döndürülen `dwMemoryLoad` `MEMORYSTATUS` `GlobalMemoryStatus`yapıdaki alanın eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="01f76-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="01f76-128">Çalışma süresi, çöp toplayıcısı için buluşsal olarak iade değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="01f76-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="01f76-129">Örneğin, ana bilgisayar belleğin çoğunluğunun kullanıldığını bildiriyorsa, çöp toplayıcı, kullanılabilir olabilecek bellek miktarını artırmak için birden çok nesilden toplamayı seçebilir.</span><span class="sxs-lookup"><span data-stu-id="01f76-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01f76-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="01f76-130">Requirements</span></span>  
 <span data-ttu-id="01f76-131">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01f76-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01f76-132">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="01f76-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="01f76-133">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="01f76-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="01f76-134">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01f76-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01f76-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="01f76-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="01f76-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="01f76-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
