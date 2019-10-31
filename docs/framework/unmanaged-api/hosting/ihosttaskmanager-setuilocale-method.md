---
title: IHostTaskManager::SetUILocale Yöntemi
ms.date: 03/30/2017
api_name:
- IHostTaskManager.SetUILocale
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostTaskManager::SetUILocale
helpviewer_keywords:
- SetUILocale method, IHostTaskManager interface [.NET Framework hosting]
- IHostTaskManager::SetUILocale method [.NET Framework hosting]
ms.assetid: d0c87a9c-ea81-4237-a16b-c22b36ec9dc8
topic_type:
- apiref
ms.openlocfilehash: a929a125fc8c70744246f4f96d8a09a4605f537c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132939"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="bcfb7-102">IHostTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcfb7-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="bcfb7-103">Ana bilgisayara, ortak dil çalışma zamanının (CLR) Şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bcfb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="bcfb7-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bcfb7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="bcfb7-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="bcfb7-106">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bcfb7-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="bcfb7-107">Return Value</span></span>  
  
|<span data-ttu-id="bcfb7-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bcfb7-108">HRESULT</span></span>|<span data-ttu-id="bcfb7-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="bcfb7-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bcfb7-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bcfb7-110">S_OK</span></span>|<span data-ttu-id="bcfb7-111">`SetUILocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="bcfb7-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bcfb7-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bcfb7-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bcfb7-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bcfb7-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bcfb7-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-115">The call timed out.</span></span>|  
|<span data-ttu-id="bcfb7-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bcfb7-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bcfb7-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bcfb7-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bcfb7-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bcfb7-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bcfb7-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="bcfb7-120">E_FAIL</span></span>|<span data-ttu-id="bcfb7-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bcfb7-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bcfb7-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bcfb7-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="bcfb7-124">E_NOTIMPL</span></span>|<span data-ttu-id="bcfb7-125">Konak, yönetilen kullanıcı kodunun UI kültürünü değiştirmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bcfb7-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="bcfb7-126">Remarks</span></span>  
 <span data-ttu-id="bcfb7-127"><xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliğinin değeri yönetilen kodla değiştirildiğinde, çalışma zamanı `SetUILocale` çağırır.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="bcfb7-128">Bu yöntem, ana bilgisayarın yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="bcfb7-129">Bir konak, Kullanıcı arabirimi yerel ayarının yönetilen koddan değiştirilmesine izin vermezse veya yerel ayarları eşitlemeye yönelik bir mekanizma uygulamaz, bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bcfb7-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="bcfb7-130">Requirements</span></span>  
 <span data-ttu-id="bcfb7-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bcfb7-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bcfb7-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="bcfb7-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bcfb7-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="bcfb7-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bcfb7-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bcfb7-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bcfb7-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="bcfb7-135">See also</span></span>

- [<span data-ttu-id="bcfb7-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcfb7-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="bcfb7-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcfb7-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="bcfb7-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcfb7-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="bcfb7-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="bcfb7-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="bcfb7-140">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="bcfb7-140">SetLocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setlocale-method.md)
