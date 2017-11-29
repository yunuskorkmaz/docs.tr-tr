---
title: ICLRGCManager::GetStats Metodu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRGCManager.GetStats
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRGCManager::GetStats
helpviewer_keywords:
- GetStats method, ICLRGCManager interface [.NET Framework hosting]
- ICLRGCManager::GetStats method [.NET Framework hosting]
ms.assetid: ce259d1d-cd81-4490-a7a1-0d0ea0804872
topic_type: apiref
caps.latest.revision: "17"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 06d52bd0348e4667f1e3ec43a371021922f12ded
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="d458e-102">ICLRGCManager::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="d458e-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="d458e-103">Ortak dil çalışma zamanı 's çöp toplama sistemi hakkında geçerli istatistiklerini kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="d458e-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d458e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d458e-104">Syntax</span></span>  
  
```  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d458e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d458e-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="d458e-106">[içinde out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) istenen istatistikleri içeren örneği.</span><span class="sxs-lookup"><span data-stu-id="d458e-106">[in, out] A [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d458e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="d458e-107">Return Value</span></span>  
  
|<span data-ttu-id="d458e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d458e-108">HRESULT</span></span>|<span data-ttu-id="d458e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d458e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d458e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="d458e-110">S_OK</span></span>|<span data-ttu-id="d458e-111">`GetStats`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="d458e-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="d458e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d458e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d458e-113">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="d458e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="d458e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="d458e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="d458e-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="d458e-115">The call timed out.</span></span>|  
|<span data-ttu-id="d458e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="d458e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="d458e-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="d458e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="d458e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="d458e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="d458e-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="d458e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="d458e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d458e-120">E_FAIL</span></span>|<span data-ttu-id="d458e-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="d458e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="d458e-122">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="d458e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="d458e-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="d458e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d458e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d458e-124">Remarks</span></span>  
 <span data-ttu-id="d458e-125">CLR hesaplar ve tarafından belirtilen istatistikleri döndürür `Flags` alanını `pStats`.</span><span class="sxs-lookup"><span data-stu-id="d458e-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="d458e-126">Ayarlama `Flags` bir veya daha fazla değerleri alan [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) hangi istatistiklerini belirtmek için numaralandırma [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) yapısı olan ayarlanacak.</span><span class="sxs-lookup"><span data-stu-id="d458e-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="d458e-127">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="d458e-127">An example of the usage is as follows:</span></span>  
  
```  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d458e-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d458e-128">Requirements</span></span>  
 <span data-ttu-id="d458e-129">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d458e-129">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d458e-130">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d458e-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d458e-131">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d458e-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d458e-132">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d458e-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d458e-133">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d458e-133">See Also</span></span>  
 [<span data-ttu-id="d458e-134">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="d458e-134">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="d458e-135">COR_GC_STATS yapısı</span><span class="sxs-lookup"><span data-stu-id="d458e-135">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="d458e-136">COR_GC_STAT_TYPES numaralandırması</span><span class="sxs-lookup"><span data-stu-id="d458e-136">COR_GC_STAT_TYPES Enumeration</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stat-types-enumeration.md)  
 [<span data-ttu-id="d458e-137">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="d458e-137">Garbage Collection</span></span>](../../../../docs/standard/garbage-collection/index.md)  
 [<span data-ttu-id="d458e-138">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="d458e-138">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="d458e-139">Iclrgcmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="d458e-139">ICLRGCManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 [<span data-ttu-id="d458e-140">CLR barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d458e-140">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)  
 [<span data-ttu-id="d458e-141">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d458e-141">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="d458e-142">Barındırma</span><span class="sxs-lookup"><span data-stu-id="d458e-142">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)
