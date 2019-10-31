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
ms.openlocfilehash: 79f24b3ccacd84037042a883d3a034bb7b4d200a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092082"
---
# <a name="iclrtaskmanagersetlocale-method"></a><span data-ttu-id="0b477-102">ICLRTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0b477-102">ICLRTaskManager::SetLocale Method</span></span>
<span data-ttu-id="0b477-103">Ana bilgisayarın şu anda yürütülmekte olan görevde yerel ayar tanımlayıcısının (coğrafi kültür ve dille eşlenir) değerini değiştirdiği ortak dil çalışma zamanına (CLR) bildirir.</span><span class="sxs-lookup"><span data-stu-id="0b477-103">Notifies the common language runtime (CLR) that the host has modified the value of the locale identifier (which maps to the geographical culture and language) on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b477-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0b477-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b477-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0b477-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="0b477-106">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="0b477-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0b477-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0b477-107">Return Value</span></span>  
  
|<span data-ttu-id="0b477-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0b477-108">HRESULT</span></span>|<span data-ttu-id="0b477-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0b477-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0b477-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="0b477-110">S_OK</span></span>|<span data-ttu-id="0b477-111">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0b477-111">The method returned successfully.</span></span>|  
|<span data-ttu-id="0b477-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0b477-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0b477-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0b477-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0b477-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0b477-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0b477-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0b477-115">The call timed out.</span></span>|  
|<span data-ttu-id="0b477-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0b477-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0b477-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="0b477-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0b477-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0b477-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0b477-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="0b477-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0b477-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="0b477-120">E_FAIL</span></span>|<span data-ttu-id="0b477-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0b477-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0b477-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0b477-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0b477-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0b477-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b477-124">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0b477-124">Remarks</span></span>  
 <span data-ttu-id="0b477-125">`SetLocale`, ana bilgisayara, yerel ayarların eşitlenmesi için sahip olabileceği mekanizmaların yürütülmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="0b477-125">`SetLocale` gives the host an opportunity to execute any mechanisms it might have for the synchronization of locales.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b477-126">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0b477-126">Requirements</span></span>  
 <span data-ttu-id="0b477-127">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b477-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b477-128">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0b477-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0b477-129">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0b477-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0b477-130">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b477-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b477-131">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0b477-131">See also</span></span>

- [<span data-ttu-id="0b477-132">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b477-132">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="0b477-133">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b477-133">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="0b477-134">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b477-134">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="0b477-135">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0b477-135">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
