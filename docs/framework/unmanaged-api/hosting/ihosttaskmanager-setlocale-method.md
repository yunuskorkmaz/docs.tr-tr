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
ms.openlocfilehash: e560d08d3e10db1b5978d1bd7be53dfed9ca3268
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132978"
---
# <a name="ihosttaskmanagersetlocale-method"></a><span data-ttu-id="ba5d1-102">IHostTaskManager::SetLocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba5d1-102">IHostTaskManager::SetLocale Method</span></span>
<span data-ttu-id="ba5d1-103">Ana bilgisayara, ortak dil çalışma zamanının (CLR) Şu anda yürütülmekte olan görevde yerel ayarı veya kültürü değiştirdiğinizi bildirir.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-103">Notifies the host that the common language runtime (CLR) has changed the locale, or culture, on the currently executing task.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba5d1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ba5d1-104">Syntax</span></span>  
  
```cpp  
HRESULT SetLocale (  
    [in] LCID lcid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ba5d1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ba5d1-105">Parameters</span></span>  
 `lcid`  
 <span data-ttu-id="ba5d1-106">'ndaki Yeni atanan coğrafi kültür ve dille eşlenen yerel ayar tanımlayıcı değeri.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-106">[in] The locale identifier value that maps to the newly assigned geographical culture and language.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ba5d1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ba5d1-107">Return Value</span></span>  
  
|<span data-ttu-id="ba5d1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ba5d1-108">HRESULT</span></span>|<span data-ttu-id="ba5d1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ba5d1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ba5d1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="ba5d1-110">S_OK</span></span>|<span data-ttu-id="ba5d1-111">`SetLocale` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-111">`SetLocale` returned successfully.</span></span>|  
|<span data-ttu-id="ba5d1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ba5d1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ba5d1-113">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="ba5d1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="ba5d1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="ba5d1-115">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-115">The call timed out.</span></span>|  
|<span data-ttu-id="ba5d1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="ba5d1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="ba5d1-117">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="ba5d1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="ba5d1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="ba5d1-119">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="ba5d1-120">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="ba5d1-120">E_FAIL</span></span>|<span data-ttu-id="ba5d1-121">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="ba5d1-122">Bir yöntem E_FAıL döndürdüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="ba5d1-123">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ba5d1-124">E_NOTIMPL</span><span class="sxs-lookup"><span data-stu-id="ba5d1-124">E_NOTIMPL</span></span>|<span data-ttu-id="ba5d1-125">Konak, yönetilen kullanıcı kodunun yerel ayarı değiştirmesine izin vermez.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-125">The host does not allow managed user code to modify the locale.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba5d1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ba5d1-126">Remarks</span></span>  
 <span data-ttu-id="ba5d1-127"><xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> özelliğinin değeri yönetilen kodla değiştirildiğinde, çalışma zamanı `SetLocale` çağırır.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-127">The runtime calls `SetLocale` when the value of the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property is changed by managed code.</span></span> <span data-ttu-id="ba5d1-128">Bu yöntem, ana bilgisayarın yerel ayarların eşitlenmesi için sahip olabileceği herhangi bir mekanizmayı yürütmesi için bir fırsat sağlar.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-128">This method provides an opportunity for the host to execute any mechanisms it might have for synchronization of locales.</span></span> <span data-ttu-id="ba5d1-129">Bir konak yerel ayarın yönetilen koddan değiştirilmesine izin vermezse veya yerel ayarları eşitlemeye yönelik bir mekanizma uygulamaz, bu yöntemden E_NOTIMPL döndürmelidir.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-129">If a host does not allow the locale to be changed from managed code, or does not implement a mechanism to synchronize locales, it should return E_NOTIMPL from this method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba5d1-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ba5d1-130">Requirements</span></span>  
 <span data-ttu-id="ba5d1-131">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba5d1-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba5d1-132">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ba5d1-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ba5d1-133">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="ba5d1-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ba5d1-134">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ba5d1-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5d1-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ba5d1-135">See also</span></span>

- [<span data-ttu-id="ba5d1-136">ICLRTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba5d1-136">ICLRTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)
- [<span data-ttu-id="ba5d1-137">ICLRTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba5d1-137">ICLRTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)
- [<span data-ttu-id="ba5d1-138">IHostTask Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba5d1-138">IHostTask Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)
- [<span data-ttu-id="ba5d1-139">IHostTaskManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ba5d1-139">IHostTaskManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)
- [<span data-ttu-id="ba5d1-140">SetUILocale Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ba5d1-140">SetUILocale Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-setuilocale-method.md)
