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
ms.openlocfilehash: e7e65c3b9bcafdf4c8b1185fcff1fc0740b2ef7c
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83841442"
---
# <a name="ihosttaskmanagersetuilocale-method"></a><span data-ttu-id="8eda9-102">IHostTaskManager::SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eda9-102">IHostTaskManager::SetUILocale Method</span></span>
<span data-ttu-id="8eda9-103">Ana bilgisayara, ortak dil çalışma zamanının (CLR) Şu anda yürütülmekte olan görevde Kullanıcı arabirimi (UI) yerel ayarını veya kültürü değiştirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="8eda9-103">Notifies the host that the common language runtime (CLR) has changed the user interface (UI) locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8eda9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8eda9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetUILocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8eda9-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8eda9-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="8eda9-106">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="8eda9-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8eda9-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8eda9-107">Return Value</span></span>  
  
|<span data-ttu-id="8eda9-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8eda9-108">HRESULT</span></span>|<span data-ttu-id="8eda9-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8eda9-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8eda9-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8eda9-110">S_OK</span></span>|<span data-ttu-id="8eda9-111">`SetUILocale`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="8eda9-111">`SetUILocale` returned successfully.</span></span>|  
|<span data-ttu-id="8eda9-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8eda9-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8eda9-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8eda9-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8eda9-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8eda9-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8eda9-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="8eda9-115">The call timed out.</span></span>|  
|<span data-ttu-id="8eda9-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8eda9-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8eda9-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="8eda9-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8eda9-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8eda9-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8eda9-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="8eda9-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8eda9-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8eda9-120">E_FAIL</span></span>|<span data-ttu-id="8eda9-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8eda9-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8eda9-122">Bir yöntem E_FAIL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8eda9-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8eda9-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8eda9-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8eda9-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="8eda9-124">E_NOTIMPL</span></span>|<span data-ttu-id="8eda9-125">Konak, yönetilen kullanıcı kodunun UI kültürünü değiştirmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="8eda9-125">The host does not allow managed user code to change the UI culture.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8eda9-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8eda9-126">Remarks</span></span>  
 <span data-ttu-id="8eda9-127">Çalışma zamanı, `SetUILocale` <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> özelliğin değeri yönetilen kod tarafından değiştirildiğinde çağrılır.</span><span class="sxs-lookup"><span data-stu-id="8eda9-127">The runtime calls `SetUILocale` when the value of the <xref:System.Threading.Thread.CurrentUICulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="8eda9-128">Bu yöntem, ana bilgisayarın yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="8eda9-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="8eda9-129">Bir konak, Kullanıcı arabirimi yerel ayarının yönetilen koddan değiştirilmesine izin vermez veya yerel ayarları eşitlemeye yönelik bir mekanizma uygulamaz, bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="8eda9-129">If a host does not allow the UI locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8eda9-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8eda9-130">Requirements</span></span>  
 <span data-ttu-id="8eda9-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8eda9-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8eda9-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8eda9-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8eda9-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8eda9-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8eda9-134">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8eda9-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eda9-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8eda9-135">See also</span></span>

- [<span data-ttu-id="8eda9-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eda9-136">ICLRTask Interface</span></span>](iclrtask-interface.md)
- [<span data-ttu-id="8eda9-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eda9-137">ICLRTaskManager Interface</span></span>](iclrtaskmanager-interface.md)
- [<span data-ttu-id="8eda9-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eda9-138">IHostTask Interface</span></span>](ihosttask-interface.md)
- [<span data-ttu-id="8eda9-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8eda9-139">IHostTaskManager Interface</span></span>](ihosttaskmanager-interface.md)
- [<span data-ttu-id="8eda9-140">SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8eda9-140">SetLocale Method</span></span>](ihosttaskmanager-setlocale-method.md)
