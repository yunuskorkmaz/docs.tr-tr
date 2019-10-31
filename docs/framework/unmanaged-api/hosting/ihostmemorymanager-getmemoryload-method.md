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
ms.openlocfilehash: 2210dcd9e8a8af92b7905ec680c53c1119e6a3cf
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136716"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="36215-102">IHostMemoryManager::GetMemoryLoad Metodu</span><span class="sxs-lookup"><span data-stu-id="36215-102">IHostMemoryManager::GetMemoryLoad Method</span></span>
<span data-ttu-id="36215-103">Şu anda kullanımda olan fiziksel bellek miktarını ve bu nedenle ana bilgisayar tarafından bildirilen kullanım sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="36215-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36215-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="36215-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,   
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36215-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="36215-105">Parameters</span></span>  
 `pMemoryLoad`  
 <span data-ttu-id="36215-106">dışı Şu anda kullanımda olan toplam fiziksel belleğin yaklaşık yüzdesine yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="36215-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="36215-107">dışı Ortak dil çalışma zamanı (CLR) için kullanılabilen bayt sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="36215-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="36215-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="36215-108">Return Value</span></span>  
  
|<span data-ttu-id="36215-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="36215-109">HRESULT</span></span>|<span data-ttu-id="36215-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="36215-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="36215-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="36215-111">S_OK</span></span>|<span data-ttu-id="36215-112">`GetMemoryLoad` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="36215-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="36215-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="36215-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="36215-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="36215-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="36215-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="36215-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="36215-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="36215-116">The call timed out.</span></span>|  
|<span data-ttu-id="36215-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="36215-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="36215-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="36215-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="36215-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="36215-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="36215-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="36215-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="36215-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="36215-121">E_FAIL</span></span>|<span data-ttu-id="36215-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="36215-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="36215-123">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="36215-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="36215-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="36215-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36215-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="36215-125">Remarks</span></span>  
 <span data-ttu-id="36215-126">`GetMemoryLoad` Win32 `GlobalMemoryStatus` işlevini sarmalar.</span><span class="sxs-lookup"><span data-stu-id="36215-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="36215-127">`pMemoryLoad` değeri, `GlobalMemoryStatus`döndürülen `MEMORYSTATUS` yapısındaki `dwMemoryLoad` alanın eşdeğeridir.</span><span class="sxs-lookup"><span data-stu-id="36215-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="36215-128">Çalışma zamanı, çöp toplayıcı için bir buluşsal yöntem olarak dönüş değerini kullanır.</span><span class="sxs-lookup"><span data-stu-id="36215-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="36215-129">Örneğin, ana bilgisayar belleğin çoğunluğunun kullanımda olduğunu bildirirse çöp toplayıcı, kullanılabilir olabilecek bellek miktarını artırmak için birden çok nesden toplamayı tercih edebilir.</span><span class="sxs-lookup"><span data-stu-id="36215-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36215-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="36215-130">Requirements</span></span>  
 <span data-ttu-id="36215-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="36215-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36215-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="36215-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="36215-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="36215-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="36215-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36215-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36215-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="36215-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="36215-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="36215-136">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
