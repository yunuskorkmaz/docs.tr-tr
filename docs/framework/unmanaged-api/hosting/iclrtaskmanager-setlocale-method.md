---
title: ICLRTaskManager::SetLocale Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, ICLRTaskManager interface [.NET Framework hosting]
- ICLRTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: ed16bb7f-4206-43a8-b9e9-c5737b69e3af
topic_type:
- apiref
ms.openlocfilehash: 5f799c140705a5279c996b6bec90ab1f29bd42ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732443"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="9cb2d-102">ICLRTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9cb2d-102">ICLRTaskManager::SetLocale Method</span></span>

<span data-ttu-id="9cb2d-103">Ana bilgisayarın şu anda yürütülmekte olan görevde yerel ayar tanımlayıcısının (coğrafi kültür ve dille eşlenir) değerini değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cb2d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="9cb2d-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9cb2d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9cb2d-105">Parameters</span></span>  

 `lcid`  
 <span data-ttu-id="9cb2d-106">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9cb2d-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9cb2d-107">Return Value</span></span>  
  
|<span data-ttu-id="9cb2d-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9cb2d-108">HRESULT</span></span>|<span data-ttu-id="9cb2d-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9cb2d-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cb2d-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="9cb2d-110">S_OK</span></span>|<span data-ttu-id="9cb2d-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="9cb2d-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9cb2d-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9cb2d-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="9cb2d-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="9cb2d-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="9cb2d-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-115">The call timed out.</span></span>|  
|<span data-ttu-id="9cb2d-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="9cb2d-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="9cb2d-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="9cb2d-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="9cb2d-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="9cb2d-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="9cb2d-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="9cb2d-120">E_FAIL</span></span>|<span data-ttu-id="9cb2d-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="9cb2d-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="9cb2d-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cb2d-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9cb2d-124">Remarks</span></span>  

 <span data-ttu-id="9cb2d-125">`SetLocale` Ana bilgisayara, yerel ayarların eşitlenmesi için sahip olabileceği mekanizmaların yürütülmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cb2d-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9cb2d-126">Requirements</span></span>  

 <span data-ttu-id="9cb2d-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cb2d-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cb2d-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9cb2d-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9cb2d-129">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="9cb2d-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9cb2d-130">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cb2d-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cb2d-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9cb2d-131">See also</span></span>

- [<span data-ttu-id="9cb2d-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9cb2d-132">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="9cb2d-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9cb2d-133">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="9cb2d-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9cb2d-134">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="9cb2d-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9cb2d-135">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
