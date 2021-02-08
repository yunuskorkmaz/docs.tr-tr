---
description: ': IHostSyncManager:: CreateRWLockReaderEvent yöntemi hakkında daha fazla bilgi edinin'
title: IHostSyncManager::CreateRWLockReaderEvent Yöntemi
ms.date: 03/30/2017
api_name:
- IHostSyncManager.CreateRWLockReaderEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSyncManager::CreateRWLockReaderEvent
helpviewer_keywords:
- CreateRWLockReaderEvent method [.NET Framework hosting]
- IHostSyncManager::CreateRWLockReaderEvent method [.NET Framework hosting]
ms.assetid: 68c4ea19-c47c-45c6-b420-d3a2ba1c2d50
topic_type:
- apiref
ms.openlocfilehash: be20757924aa45d2a44edab9bf921026aa0247a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784775"
---
# <a name="ihostsyncmanagercreaterwlockreaderevent-method"></a><span data-ttu-id="fee71-103">IHostSyncManager::CreateRWLockReaderEvent Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fee71-103">IHostSyncManager::CreateRWLockReaderEvent Method</span></span>

<span data-ttu-id="fee71-104">Bir okuyucu kilidinin uygulanması için el ile sıfırlama olay nesnesi oluşturur.</span><span class="sxs-lookup"><span data-stu-id="fee71-104">Creates a manual-reset event object for the implementation of a reader lock.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fee71-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fee71-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateRWLockReaderEvent (  
    [in]  BOOL bInitialState,  
    [in]  SIZE_T cookie,  
    [out] IHostManualEvent **ppEvent  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fee71-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fee71-106">Parameters</span></span>  

 `bInitialState`  
 <span data-ttu-id="fee71-107">[in] `true` , `ppEvent` sinyal alınmalıdır; Aksi takdirde, `false` .</span><span class="sxs-lookup"><span data-stu-id="fee71-107">[in] `true`, if `ppEvent` should be signaled; otherwise, `false`.</span></span>  
  
 `cookie`  
 <span data-ttu-id="fee71-108">'ndaki Okuyucu kilidi ile ilişkilendirilecek tanımlama bilgisi.</span><span class="sxs-lookup"><span data-stu-id="fee71-108">[in] A cookie to associate with the reader lock.</span></span>  
  
 `ppEvent`  
 <span data-ttu-id="fee71-109">dışı Bir [IHostManualEvent](ihostmanualevent-interface.md) örneğinin adresine yönelik bir işaretçi veya olay nesnesi oluşturuoluşturulamadığı null.</span><span class="sxs-lookup"><span data-stu-id="fee71-109">[out] A pointer to the address of an [IHostManualEvent](ihostmanualevent-interface.md) instance, or null if the event object could not be created.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fee71-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fee71-110">Return Value</span></span>  
  
|<span data-ttu-id="fee71-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fee71-111">HRESULT</span></span>|<span data-ttu-id="fee71-112">Description</span><span class="sxs-lookup"><span data-stu-id="fee71-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fee71-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="fee71-113">S_OK</span></span>|<span data-ttu-id="fee71-114">`CreateRWLockReaderEvent` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="fee71-114">`CreateRWLockReaderEvent` returned successfully.</span></span>|  
|<span data-ttu-id="fee71-115">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fee71-115">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fee71-116">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fee71-116">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fee71-117">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fee71-117">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fee71-118">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="fee71-118">The call timed out.</span></span>|  
|<span data-ttu-id="fee71-119">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fee71-119">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fee71-120">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="fee71-120">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fee71-121">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fee71-121">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fee71-122">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="fee71-122">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fee71-123">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fee71-123">E_FAIL</span></span>|<span data-ttu-id="fee71-124">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fee71-124">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fee71-125">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fee71-125">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fee71-126">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fee71-126">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fee71-127">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="fee71-127">E_OUTOFMEMORY</span></span>|<span data-ttu-id="fee71-128">İstenen olay nesnesini oluşturmak için yeterli bellek yok.</span><span class="sxs-lookup"><span data-stu-id="fee71-128">Not enough memory was available to create the requested event object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fee71-129">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fee71-129">Remarks</span></span>  

 <span data-ttu-id="fee71-130">CLR, `CreateRWLockReaderEvent` `IHostManualEvent` bir okuyucu kilidi uygulamasında kullanmak üzere bir örneğe başvuru almak için çağırır.</span><span class="sxs-lookup"><span data-stu-id="fee71-130">The CLR calls `CreateRWLockReaderEvent` to get a reference to an `IHostManualEvent` instance to use in its implementation of a reader lock.</span></span> <span data-ttu-id="fee71-131">Ana bilgisayar, [ICLRSyncManager](iclrsyncmanager-interface.md) arabirimini sorgulayarak okuyucu kilidinde hangi görevlerin beklediğini belirleyen tanımlama bilgisini kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="fee71-131">The host can use the cookie to determine which tasks are waiting on the reader lock by querying the [ICLRSyncManager](iclrsyncmanager-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fee71-132">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fee71-132">Requirements</span></span>  

 <span data-ttu-id="fee71-133">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fee71-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fee71-134">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fee71-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fee71-135">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fee71-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fee71-136">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fee71-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee71-137">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fee71-137">See also</span></span>

- [<span data-ttu-id="fee71-138">ICLRSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fee71-138">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="fee71-139">IHostAutoEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fee71-139">IHostAutoEvent Interface</span></span>](ihostautoevent-interface.md)
- [<span data-ttu-id="fee71-140">IHostManualEvent Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fee71-140">IHostManualEvent Interface</span></span>](ihostmanualevent-interface.md)
- [<span data-ttu-id="fee71-141">IHostSyncManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fee71-141">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
