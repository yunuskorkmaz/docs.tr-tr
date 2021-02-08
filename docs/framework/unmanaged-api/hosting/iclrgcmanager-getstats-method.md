---
description: ': ICLRGCManager:: GetStats yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 94b20fb313f06d73f1e7fafd1f46fefb0da3fe95
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790028"
---
# <a name="iclrgcmanagergetstats-method"></a><span data-ttu-id="43f94-103">ICLRGCManager::GetStats Metodu</span><span class="sxs-lookup"><span data-stu-id="43f94-103">ICLRGCManager::GetStats Method</span></span>

<span data-ttu-id="43f94-104">Ortak dil çalışma zamanının çöp toplama sistemiyle ilgili geçerli istatistik kümesini alır.</span><span class="sxs-lookup"><span data-stu-id="43f94-104">Gets a set of current statistics about the common language runtime's garbage collection system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f94-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="43f94-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStats (  
    [in, out] COR_GC_STATS *pStats  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="43f94-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="43f94-106">Parameters</span></span>  

 `pStats`  
 <span data-ttu-id="43f94-107">[in, out] İstenen istatistikleri içeren bir [cor_gc_stats](cor-gc-stats-structure.md) örneği.</span><span class="sxs-lookup"><span data-stu-id="43f94-107">[in, out] A [COR_GC_STATS](cor-gc-stats-structure.md) instance that contains the requested statistics.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="43f94-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="43f94-108">Return Value</span></span>  
  
|<span data-ttu-id="43f94-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="43f94-109">HRESULT</span></span>|<span data-ttu-id="43f94-110">Description</span><span class="sxs-lookup"><span data-stu-id="43f94-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="43f94-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="43f94-111">S_OK</span></span>|<span data-ttu-id="43f94-112">`GetStats` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="43f94-112">`GetStats` returned successfully.</span></span>|  
|<span data-ttu-id="43f94-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="43f94-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="43f94-114">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="43f94-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="43f94-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="43f94-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="43f94-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="43f94-116">The call timed out.</span></span>|  
|<span data-ttu-id="43f94-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="43f94-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="43f94-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="43f94-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="43f94-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="43f94-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="43f94-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="43f94-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="43f94-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="43f94-121">E_FAIL</span></span>|<span data-ttu-id="43f94-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="43f94-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="43f94-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="43f94-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="43f94-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="43f94-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43f94-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="43f94-125">Remarks</span></span>  

 <span data-ttu-id="43f94-126">CLR, yalnızca alanı tarafından belirtilen istatistikleri hesaplar ve döndürür `Flags` `pStats` .</span><span class="sxs-lookup"><span data-stu-id="43f94-126">The CLR calculates and returns only those statistics that are specified by the `Flags` field of `pStats`.</span></span>  
  
 <span data-ttu-id="43f94-127">`Flags` [Cor_gc_stats](cor-gc-stats-structure.md) yapısındaki hangi istatistiklerin ayarlanacağını belirtmek için alanı [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) numaralandırmanın bir veya daha fazla değerine ayarlayın.</span><span class="sxs-lookup"><span data-stu-id="43f94-127">Set the `Flags` field to one or more values of the [COR_GC_STAT_TYPES](cor-gc-stat-types-enumeration.md) enumeration to specify which statistics in the [COR_GC_STATS](cor-gc-stats-structure.md) structure are to be set.</span></span>  
  
 <span data-ttu-id="43f94-128">Kullanım örneği aşağıdaki gibidir:</span><span class="sxs-lookup"><span data-stu-id="43f94-128">An example of the usage is as follows:</span></span>  
  
```cpp  
COR_GC_STATS GCStats;  
GCStats.Flags = COR_GC_COUNTS | COR_GC_MEMORYUSAGE;  
pCLRGCManager->GetStats(&GCStats);  
```  
  
## <a name="requirements"></a><span data-ttu-id="43f94-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="43f94-129">Requirements</span></span>  

 <span data-ttu-id="43f94-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43f94-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43f94-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="43f94-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="43f94-132">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="43f94-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="43f94-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43f94-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f94-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="43f94-134">See also</span></span>

- [<span data-ttu-id="43f94-135">Otomatik bellek yönetimi</span><span class="sxs-lookup"><span data-stu-id="43f94-135">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="43f94-136">COR_GC_STATS Yapısı</span><span class="sxs-lookup"><span data-stu-id="43f94-136">COR_GC_STATS Structure</span></span>](cor-gc-stats-structure.md)
- [<span data-ttu-id="43f94-137">COR_GC_STAT_TYPES Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="43f94-137">COR_GC_STAT_TYPES Enumeration</span></span>](cor-gc-stat-types-enumeration.md)
- [<span data-ttu-id="43f94-138">Çöp toplama</span><span class="sxs-lookup"><span data-stu-id="43f94-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="43f94-139">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43f94-139">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="43f94-140">ICLRGCManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="43f94-140">ICLRGCManager Interface</span></span>](iclrgcmanager-interface.md)
- [<span data-ttu-id="43f94-141">CLR Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43f94-141">CLR Hosting Interfaces</span></span>](clr-hosting-interfaces.md)
- [<span data-ttu-id="43f94-142">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="43f94-142">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="43f94-143">Hosting</span><span class="sxs-lookup"><span data-stu-id="43f94-143">Hosting</span></span>](index.md)
