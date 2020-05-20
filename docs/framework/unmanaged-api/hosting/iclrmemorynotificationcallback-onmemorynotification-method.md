---
title: ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback.OnMemoryNotification
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification
helpviewer_keywords:
- ICLRMemoryNotificationCallback::OnMemoryNotification method [.NET Framework hosting]
- OnMemoryNotification method [.NET Framework hosting]
ms.assetid: 5612a44d-56cc-4f34-af31-8c9809ba9431
topic_type:
- apiref
ms.openlocfilehash: d88abcc523eca06c8ec50cac2d2984b26099174a
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703797"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="144d0-102">ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="144d0-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="144d0-103">Bilgisayardaki bellek yükünün ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="144d0-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144d0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="144d0-104">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="144d0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="144d0-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="144d0-106">'ndaki Bilgisayarın şu anda karşılaştığı bellek basıncını gösteren [EMemoryAvailable](ememoryavailable-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="144d0-106">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="144d0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="144d0-107">Return Value</span></span>  
  
|<span data-ttu-id="144d0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="144d0-108">HRESULT</span></span>|<span data-ttu-id="144d0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="144d0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="144d0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="144d0-110">S_OK</span></span>|<span data-ttu-id="144d0-111">`OnMemoryNotification`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="144d0-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="144d0-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="144d0-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="144d0-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="144d0-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="144d0-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="144d0-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="144d0-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="144d0-115">The call timed out.</span></span>|  
|<span data-ttu-id="144d0-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="144d0-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="144d0-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="144d0-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="144d0-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="144d0-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="144d0-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="144d0-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="144d0-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="144d0-120">E_FAIL</span></span>|<span data-ttu-id="144d0-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="144d0-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="144d0-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="144d0-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="144d0-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="144d0-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="144d0-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="144d0-124">Remarks</span></span>  
 <span data-ttu-id="144d0-125">CLR, `OnMemoryNotification` [IHostMemoryManager:: RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) yöntemine bir çağrı kullanarak öğesine bir geri çağırma kaydeder.</span><span class="sxs-lookup"><span data-stu-id="144d0-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="144d0-126">Çalışma zamanı, ana bilgisayar bellek kaynaklarının düşük çalıştığını bildirdiğinde ek belleği boşaltmak için geri çağırmada döndürülen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="144d0-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="144d0-127">Hiçbir şekilde `OnMemoryNotification` engellenmemek için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="144d0-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="144d0-128">Her zaman hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="144d0-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144d0-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="144d0-129">Requirements</span></span>  
 <span data-ttu-id="144d0-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144d0-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144d0-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="144d0-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="144d0-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="144d0-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="144d0-133">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144d0-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144d0-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="144d0-134">See also</span></span>

- [<span data-ttu-id="144d0-135">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="144d0-135">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="144d0-136">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="144d0-136">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="144d0-137">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="144d0-137">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
