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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 187c0a8d929958b7eaf1e99771da6a0d29c3d5f7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33434193"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="9ed9e-102">ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ed9e-102">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>
<span data-ttu-id="9ed9e-103">Ortak dil çalışma zamanı (CLR) bilgisayardaki Bellek Yükü bildirir.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-103">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ed9e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ed9e-104">Syntax</span></span>  
  
```  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9ed9e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9ed9e-105">Parameters</span></span>  
 `eMemoryAvailable`  
 <span data-ttu-id="9ed9e-106">[in] Aşağıdakilerden birini [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) değerleri, bellek baskısı bilgisayar belirten şu anda karşılaşılan.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-106">[in] One of the [EMemoryAvailable](../../../../docs/framework/unmanaged-api/hosting/ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9ed9e-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9ed9e-107">Return Value</span></span>  
  
|<span data-ttu-id="9ed9e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9ed9e-108">HRESULT</span></span>|<span data-ttu-id="9ed9e-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9ed9e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9ed9e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9ed9e-110">S_OK</span></span>|<span data-ttu-id="9ed9e-111">`OnMemoryNotification` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-111">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="9ed9e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9ed9e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9ed9e-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9ed9e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9ed9e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9ed9e-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-115">The call timed out.</span></span>|  
|<span data-ttu-id="9ed9e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9ed9e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9ed9e-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9ed9e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9ed9e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9ed9e-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9ed9e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9ed9e-120">E_FAIL</span></span>|<span data-ttu-id="9ed9e-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9ed9e-122">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-122">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9ed9e-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ed9e-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9ed9e-124">Remarks</span></span>  
 <span data-ttu-id="9ed9e-125">CLR için bir geri çağırma kaydeder `OnMemoryNotification` yapılan bir çağrı kullanılarak [Ihostmemorymanager::registermemorynotificationcallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-125">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="9ed9e-126">Çalışma zamanı ana bilgisayarın bu bellek kaynakları düşük çalıştıran bildirdiğinde ek bellek boşaltmak için geri döndürülen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-126">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9ed9e-127">Çağrılar `OnMemoryNotification` hiçbir zaman engelleyin.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-127">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="9ed9e-128">Bunlar her zaman hemen döndürür.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-128">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ed9e-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ed9e-129">Requirements</span></span>  
 <span data-ttu-id="9ed9e-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ed9e-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ed9e-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9ed9e-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ed9e-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9ed9e-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ed9e-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ed9e-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ed9e-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="9ed9e-134">See Also</span></span>  
 [<span data-ttu-id="9ed9e-135">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ed9e-135">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="9ed9e-136">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ed9e-136">RegisterMemoryNotificationCallback Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-registermemorynotificationcallback-method.md)  
 [<span data-ttu-id="9ed9e-137">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ed9e-137">ICLRMemoryNotificationCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)
