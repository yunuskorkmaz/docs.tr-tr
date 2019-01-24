---
title: ICLRRuntimeHost::SetHostControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.SetHostControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e385744f1a9ecef2cbe1f6074501061dc2f15fe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602266"
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="4bdc5-102">ICLRRuntimeHost::SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4bdc5-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="4bdc5-103">Ortak dil çalışma zamanı (CLR), konağın uygulamasını almak için kullanabileceğiniz bir arabirim işaretçisini ayarlar [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4bdc5-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bdc5-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4bdc5-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4bdc5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4bdc5-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="4bdc5-106">[in] Ana bilgisayarın uygulaması için bir arabirim işaretçisi [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4bdc5-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bdc5-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4bdc5-107">Return Value</span></span>  
  
|<span data-ttu-id="4bdc5-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bdc5-108">HRESULT</span></span>|<span data-ttu-id="4bdc5-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4bdc5-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bdc5-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bdc5-110">S_OK</span></span>|<span data-ttu-id="4bdc5-111">`SetHostControl` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="4bdc5-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bdc5-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bdc5-113">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bdc5-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bdc5-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bdc5-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-115">The call timed out.</span></span>|  
|<span data-ttu-id="4bdc5-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bdc5-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bdc5-117">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bdc5-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bdc5-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bdc5-119">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bdc5-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bdc5-120">E_FAIL</span></span>|<span data-ttu-id="4bdc5-121">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bdc5-122">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bdc5-123">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4bdc5-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="4bdc5-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="4bdc5-125">CLR zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bdc5-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4bdc5-126">Remarks</span></span>  
 <span data-ttu-id="4bdc5-127">Çağırmalısınız `SetHostControl` çağırmadan önce CLR, yani başlatılmadan önce [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) veya herhangi birini kullanan [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="4bdc5-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="4bdc5-128">Önerilen çağırmanızı `SetHostControl` arama hemen sonra [CorBindToCurrentRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) veya [CorBindToRuntimeEx işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="4bdc5-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bdc5-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4bdc5-129">Requirements</span></span>  
 <span data-ttu-id="4bdc5-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bdc5-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bdc5-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4bdc5-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bdc5-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4bdc5-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bdc5-133">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bdc5-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bdc5-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4bdc5-134">See also</span></span>
- [<span data-ttu-id="4bdc5-135">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bdc5-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="4bdc5-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4bdc5-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
