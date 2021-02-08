---
description: ': ICLRMemoryNotificationCallback:: OnMemoryNotification yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 92041c433fa82bb63afda7968eb8c6e1fa72acb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789922"
---
# <a name="iclrmemorynotificationcallbackonmemorynotification-method"></a><span data-ttu-id="dc65c-103">ICLRMemoryNotificationCallback::OnMemoryNotification Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc65c-103">ICLRMemoryNotificationCallback::OnMemoryNotification Method</span></span>

<span data-ttu-id="dc65c-104">Bilgisayardaki bellek yükünün ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="dc65c-104">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc65c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dc65c-105">Syntax</span></span>  
  
```cpp  
HRESULT OnMemoryNotification (  
    [in] EMemoryAvailable eMemoryAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dc65c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dc65c-106">Parameters</span></span>  

 `eMemoryAvailable`  
 <span data-ttu-id="dc65c-107">'ndaki Bilgisayarın şu anda karşılaştığı bellek basıncını gösteren [EMemoryAvailable](ememoryavailable-enumeration.md) değerlerinden biri.</span><span class="sxs-lookup"><span data-stu-id="dc65c-107">[in] One of the [EMemoryAvailable](ememoryavailable-enumeration.md) values, indicating the memory pressure the computer is currently experiencing.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dc65c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="dc65c-108">Return Value</span></span>  
  
|<span data-ttu-id="dc65c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dc65c-109">HRESULT</span></span>|<span data-ttu-id="dc65c-110">Description</span><span class="sxs-lookup"><span data-stu-id="dc65c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dc65c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="dc65c-111">S_OK</span></span>|<span data-ttu-id="dc65c-112">`OnMemoryNotification` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="dc65c-112">`OnMemoryNotification` returned successfully.</span></span>|  
|<span data-ttu-id="dc65c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dc65c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dc65c-114">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="dc65c-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dc65c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dc65c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dc65c-116">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="dc65c-116">The call timed out.</span></span>|  
|<span data-ttu-id="dc65c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dc65c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dc65c-118">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="dc65c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dc65c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dc65c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dc65c-120">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="dc65c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dc65c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dc65c-121">E_FAIL</span></span>|<span data-ttu-id="dc65c-122">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="dc65c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dc65c-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="dc65c-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dc65c-124">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="dc65c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dc65c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dc65c-125">Remarks</span></span>  

 <span data-ttu-id="dc65c-126">CLR, `OnMemoryNotification` [IHostMemoryManager:: RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) yöntemine bir çağrı kullanarak öğesine bir geri çağırma kaydeder.</span><span class="sxs-lookup"><span data-stu-id="dc65c-126">The CLR registers a callback to `OnMemoryNotification` by using a call to the [IHostMemoryManager::RegisterMemoryNotificationCallback](ihostmemorymanager-registermemorynotificationcallback-method.md) method.</span></span> <span data-ttu-id="dc65c-127">Çalışma zamanı, ana bilgisayar bellek kaynaklarının düşük çalıştığını bildirdiğinde ek belleği boşaltmak için geri çağırmada döndürülen bilgileri kullanır.</span><span class="sxs-lookup"><span data-stu-id="dc65c-127">The runtime uses the information returned in the callback to free additional memory when the host reports that memory resources are running low.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="dc65c-128">Hiçbir şekilde `OnMemoryNotification` engellenmemek için çağrılar.</span><span class="sxs-lookup"><span data-stu-id="dc65c-128">Calls to `OnMemoryNotification` never block.</span></span> <span data-ttu-id="dc65c-129">Her zaman hemen döndürülür.</span><span class="sxs-lookup"><span data-stu-id="dc65c-129">They always return immediately.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc65c-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dc65c-130">Requirements</span></span>  

 <span data-ttu-id="dc65c-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dc65c-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dc65c-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dc65c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dc65c-133">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="dc65c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dc65c-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dc65c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc65c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dc65c-135">See also</span></span>

- [<span data-ttu-id="dc65c-136">IHostMemoryManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc65c-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="dc65c-137">RegisterMemoryNotificationCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dc65c-137">RegisterMemoryNotificationCallback Method</span></span>](ihostmemorymanager-registermemorynotificationcallback-method.md)
- [<span data-ttu-id="dc65c-138">ICLRMemoryNotificationCallback Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dc65c-138">ICLRMemoryNotificationCallback Interface</span></span>](iclrmemorynotificationcallback-interface.md)
