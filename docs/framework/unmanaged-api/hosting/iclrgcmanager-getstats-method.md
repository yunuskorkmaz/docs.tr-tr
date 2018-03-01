---
title: ICLRGCManager::GetStats Metodu
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c6ba88eebb963749247b318f14ef52bb116e3f0c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="13fc6-102">ICLRGCManager::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="13fc6-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="13fc6-103">Ortak dil çalışma zamanı 's çöp toplama sistemi hakkında geçerli istatistiklerini kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="13fc6-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13fc6-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="13fc6-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="13fc6-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="13fc6-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="13fc6-106">[içinde out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) istenen istatistikleri içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="13fc6-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13fc6-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="13fc6-107">Return Value</span></span>  
  
|<span data-ttu-id="13fc6-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="13fc6-108">HRESULT</span></span>|<span data-ttu-id="13fc6-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="13fc6-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="13fc6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="13fc6-110">S_OK</span></span>|<span data-ttu-id="13fc6-111">`GetStats`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="13fc6-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="13fc6-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="13fc6-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="13fc6-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="13fc6-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="13fc6-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="13fc6-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="13fc6-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="13fc6-115">The call timed out.</span></span>|  
|<span data-ttu-id="13fc6-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="13fc6-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="13fc6-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="13fc6-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="13fc6-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="13fc6-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="13fc6-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="13fc6-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="13fc6-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="13fc6-120">E_FAIL</span></span>|<span data-ttu-id="13fc6-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="13fc6-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="13fc6-122">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="13fc6-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="13fc6-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="13fc6-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13fc6-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="13fc6-124">Remarks</span></span>  
 <span data-ttu-id="13fc6-125">CLR hesaplar ve tarafından belirtilen istatistikleri döndürür `Flags` alanını `pStats`.</span><span class="sxs-lookup"><span data-stu-id="13fc6-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="13fc6-126">Ayarlama `Flags` bir veya daha fazla değerleri alan [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) hangi istatistiklerini belirtmek için numaralandırma [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısı olan ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="13fc6-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="13fc6-127">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="13fc6-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="13fc6-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="13fc6-128">Requirements</span></span>  
 <span data-ttu-id="13fc6-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13fc6-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13fc6-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="13fc6-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="13fc6-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="13fc6-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="13fc6-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13fc6-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13fc6-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="13fc6-133">See Also</span></span>  
 [<span data-ttu-id="13fc6-134">Otomatik Bellek Yönetimi</span><span class="sxs-lookup"><span data-stu-id="13fc6-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="13fc6-135">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="13fc6-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="13fc6-136">COR_GC_STAT_TYPES Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="13fc6-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="13fc6-137">Atık Toplama</span><span class="sxs-lookup"><span data-stu-id="13fc6-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="13fc6-138">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13fc6-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="13fc6-139">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="13fc6-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="13fc6-140">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="13fc6-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="13fc6-141">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="13fc6-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="13fc6-142">Barındırma</span><span class="sxs-lookup"><span data-stu-id="13fc6-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
