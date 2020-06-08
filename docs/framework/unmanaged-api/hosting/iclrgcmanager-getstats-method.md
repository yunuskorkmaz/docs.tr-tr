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
ms.openlocfilehash: 8622920a81f4b469361ffa879f7a4eeda697cab9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504231"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="7bb79-102">ICLRGCManager::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="7bb79-102">ICLRGCManager::GetStats Method</span></span>
<span data-ttu-id="7bb79-103">Ortak dil çalışma zamanının çöp toplama sistemiyle ilgili geçerli istatistik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="7bb79-103">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bb79-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7bb79-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bb79-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="7bb79-105">Parameters</span></span>  
 `pStats`  
 <span data-ttu-id="7bb79-106">[in, out] İstenen istatistikleri içeren bir [cor_gc_stats](cor-gc-stats-structure.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="7bb79-106">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7bb79-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="7bb79-107">Return Value</span></span>  
  
|<span data-ttu-id="7bb79-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7bb79-108">HRESULT</span></span>|<span data-ttu-id="7bb79-109">Description</span><span class="sxs-lookup"><span data-stu-id="7bb79-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7bb79-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7bb79-110">S_OK</span></span>|<span data-ttu-id="7bb79-111">`GetStats`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="7bb79-111">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="7bb79-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7bb79-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7bb79-113">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="7bb79-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="7bb79-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="7bb79-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="7bb79-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="7bb79-115">The call timed out.</span></span>|  
|<span data-ttu-id="7bb79-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="7bb79-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="7bb79-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="7bb79-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="7bb79-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="7bb79-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="7bb79-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="7bb79-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="7bb79-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7bb79-120">E_FAIL</span></span>|<span data-ttu-id="7bb79-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="7bb79-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="7bb79-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="7bb79-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="7bb79-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="7bb79-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bb79-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7bb79-124">Remarks</span></span>  
 <span data-ttu-id="7bb79-125">CLR, yalnızca alanı tarafından belirtilen istatistikleri hesaplar ve döndürür `Flags` `pStats` .</span><span class="sxs-lookup"><span data-stu-id="7bb79-125">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="7bb79-126">`Flags` [Cor_gc_stats](cor-gc-stats-structure.md) yapısındaki hangi istatistiklerin ayarlanacağını belirtmek için alanı [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) numaralandırmanın bir veya daha fazla değerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="7bb79-126">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="7bb79-127">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="7bb79-127">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7bb79-128">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7bb79-128">Requirements</span></span>  
 <span data-ttu-id="7bb79-129">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7bb79-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7bb79-130">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7bb79-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7bb79-131">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7bb79-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7bb79-132">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7bb79-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bb79-133">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7bb79-133">See also</span></span>

- [<span data-ttu-id="7bb79-134">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="7bb79-134">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="7bb79-135">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="7bb79-135">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="7bb79-136">COR_GC_STAT_TYPES Sabit Listesi</span><span class="sxs-lookup"><span data-stu-id="7bb79-136">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="7bb79-137">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="7bb79-137">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="7bb79-138">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bb79-138">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="7bb79-139">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7bb79-139">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="7bb79-140">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7bb79-140">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="7bb79-141">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="7bb79-141">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="7bb79-142">Hosting</span><span class="sxs-lookup"><span data-stu-id="7bb79-142">Hosting</span></span>](index.md)
