---
title: ICLRGCManager::GetStats Metodu
ms.date: 03/30/2017
api_name:
- ICLRGCManager.GetStats
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 768d16a05bbe139c3fe02677526bc28809a93be0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779725"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="04aef-102">ICLRGCManager::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="04aef-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="04aef-103">Ortak dil çalışma zamanının atık toplama sistemi geçerli İstatistikler kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="04aef-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04aef-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="04aef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="04aef-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="04aef-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="04aef-106">[out içinde] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) istenen istatistikleri içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="04aef-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04aef-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="04aef-107">Return Value</span></span>  
  
|<span data-ttu-id="04aef-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="04aef-108">HRESULT</span></span>|<span data-ttu-id="04aef-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="04aef-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="04aef-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="04aef-110">S_OK</span></span>|<span data-ttu-id="04aef-111">`GetStats` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="04aef-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="04aef-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="04aef-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="04aef-113">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="04aef-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="04aef-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="04aef-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="04aef-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="04aef-115">The call timed out.</span></span>|  
|<span data-ttu-id="04aef-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="04aef-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="04aef-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="04aef-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="04aef-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="04aef-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="04aef-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="04aef-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="04aef-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="04aef-120">E_FAIL</span></span>|<span data-ttu-id="04aef-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="04aef-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="04aef-122">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="04aef-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="04aef-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="04aef-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04aef-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="04aef-124">Remarks</span></span>  
 <span data-ttu-id="04aef-125">CLR hesaplar ve döndürür tarafından belirtilen istatistikleri `Flags` alanını `pStats`.</span><span class="sxs-lookup"><span data-stu-id="04aef-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="04aef-126">Ayarlama `Flags` bir veya daha fazla değer alanı [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) hangi istatistikleri belirtmek için sabit listesi [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısı olan ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="04aef-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="04aef-127">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="04aef-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="04aef-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="04aef-128">Requirements</span></span>  
 <span data-ttu-id="04aef-129">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04aef-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04aef-130">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="04aef-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="04aef-131">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="04aef-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="04aef-132">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04aef-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04aef-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="04aef-133">See also</span></span>

- [<span data-ttu-id="04aef-134">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="04aef-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="04aef-135">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="04aef-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="04aef-136">COR_GC_STAT_TYPES Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="04aef-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="04aef-137">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="04aef-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)
- [<span data-ttu-id="04aef-138">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04aef-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="04aef-139">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="04aef-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)
- [<span data-ttu-id="04aef-140">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04aef-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="04aef-141">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="04aef-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="04aef-142">Barındırma</span><span class="sxs-lookup"><span data-stu-id="04aef-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
