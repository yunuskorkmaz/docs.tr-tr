---
title: IHostTaskManager::SetLocale Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetLocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetLocale
helpviewer_keywords:
- SetLocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetLocale method [.NET Framework hosting]
ms.assetid: 747ee407-ee8c-484d-9583-25089236d2d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af9a8939c2ff50eb41b4f5c14097751fdc92ff83
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33443147"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="f36f2-102">IHostTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f36f2-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="f36f2-103">Ortak dil çalışma zamanı (CLR) yerel ya da şu anda yürütülen görevde kültürü değişti konak bildirir.</span><span class="sxs-lookup"><span data-stu-id="f36f2-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f36f2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f36f2-104">Syntax</span></span>  
  
```  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f36f2-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f36f2-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="f36f2-106">[in] Yeni atanan coğrafi kültür ve dil eşler yerel ayar tanımlayıcısı değeri.</span><span class="sxs-lookup"><span data-stu-id="f36f2-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f36f2-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="f36f2-107">Return Value</span></span>  
  
|<span data-ttu-id="f36f2-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f36f2-108">HRESULT</span></span>|<span data-ttu-id="f36f2-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f36f2-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f36f2-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f36f2-110">S_OK</span></span>|<span data-ttu-id="f36f2-111">`SetLocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="f36f2-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="f36f2-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="f36f2-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="f36f2-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="f36f2-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="f36f2-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="f36f2-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="f36f2-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="f36f2-115">The call timed out.</span></span>|  
|<span data-ttu-id="f36f2-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="f36f2-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="f36f2-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="f36f2-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="f36f2-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="f36f2-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="f36f2-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="f36f2-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="f36f2-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="f36f2-120">E_FAIL</span></span>|<span data-ttu-id="f36f2-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="f36f2-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="f36f2-122">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="f36f2-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="f36f2-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="f36f2-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="f36f2-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="f36f2-124">E_NOTIMPL</span></span>|<span data-ttu-id="f36f2-125">Ana bilgisayarın yerel ayarı değiştirmek yönetilen kullanıcı kodu izin vermiyor.</span><span class="sxs-lookup"><span data-stu-id="f36f2-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f36f2-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f36f2-126">Remarks</span></span>  
 <span data-ttu-id="f36f2-127">Çalışma zamanı çağrıları `SetLocale` zaman değerini <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliği tarafından yönetilen kod değiştirildi.</span><span class="sxs-lookup"><span data-stu-id="f36f2-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="f36f2-128">Bu yöntem, sahip olabilirsiniz herhangi bir mekanizması yerel ayarlar eşitlenmesi için yürütmek ana bilgisayar için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="f36f2-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="f36f2-129">Bir konak yerel yönetilen koddan değiştirilmesine izin vermez veya yerel ayarlar eşitlemek için bir mekanizma uygulamaz, bu yöntemle E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="f36f2-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f36f2-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f36f2-130">Requirements</span></span>  
 <span data-ttu-id="f36f2-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f36f2-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f36f2-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f36f2-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f36f2-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f36f2-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f36f2-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f36f2-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f36f2-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f36f2-135">See Also</span></span>  
 [<span data-ttu-id="f36f2-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f36f2-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 [<span data-ttu-id="f36f2-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f36f2-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 [<span data-ttu-id="f36f2-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f36f2-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 [<span data-ttu-id="f36f2-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f36f2-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 [<span data-ttu-id="f36f2-140">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f36f2-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
