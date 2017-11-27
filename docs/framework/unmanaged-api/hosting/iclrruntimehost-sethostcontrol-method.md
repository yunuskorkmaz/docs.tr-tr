---
title: "ICLRRuntimeHost::SetHostControl Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.SetHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::SetHostControl
helpviewer_keywords:
- SetHostControl method [.NET Framework hosting]
- ICLRRuntimeHost::SetHostControl method [.NET Framework hosting]
ms.assetid: 6136be87-e631-4756-81ed-74b66581bad4
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 932ba5577ee262b2b044fe5cd7681de1f8b459f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrruntimehostsethostcontrol-method"></a><span data-ttu-id="21ce1-102">ICLRRuntimeHost::SetHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="21ce1-102">ICLRRuntimeHost::SetHostControl Method</span></span>
<span data-ttu-id="21ce1-103">Ortak dil çalışma zamanı (CLR) ana bilgisayarın uyarlamasını elde etmek için kullanabileceğiniz arabirim işaretçisi ayarlar [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-103">Sets the interface pointer that the common language runtime (CLR) can use to get the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21ce1-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="21ce1-104">Syntax</span></span>  
  
```  
HRESULT SetHostControl(  
    [in] IHostControl* pHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21ce1-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="21ce1-105">Parameters</span></span>  
 `pHostControl`  
 <span data-ttu-id="21ce1-106">[in] Ana bilgisayarın uygulaması için bir arabirim işaretçisi [Ihostcontrol arabirimi](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-106">[in] An interface pointer to the host's implementation of [IHostControl Interface](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21ce1-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="21ce1-107">Return Value</span></span>  
  
|<span data-ttu-id="21ce1-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21ce1-108">HRESULT</span></span>|<span data-ttu-id="21ce1-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="21ce1-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21ce1-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="21ce1-110">S_OK</span></span>|<span data-ttu-id="21ce1-111">`SetHostControl`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="21ce1-111">`SetHostControl` returned successfully.</span></span>|  
|<span data-ttu-id="21ce1-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21ce1-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21ce1-113">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="21ce1-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="21ce1-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="21ce1-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="21ce1-115">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="21ce1-115">The call timed out.</span></span>|  
|<span data-ttu-id="21ce1-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="21ce1-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="21ce1-117">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="21ce1-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="21ce1-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="21ce1-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="21ce1-119">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="21ce1-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="21ce1-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21ce1-120">E_FAIL</span></span>|<span data-ttu-id="21ce1-121">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="21ce1-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="21ce1-122">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="21ce1-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="21ce1-123">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="21ce1-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21ce1-124">E_CLR_ALREADY_STARTED</span><span class="sxs-lookup"><span data-stu-id="21ce1-124">E_CLR_ALREADY_STARTED</span></span>|<span data-ttu-id="21ce1-125">CLR zaten başlatıldı.</span><span class="sxs-lookup"><span data-stu-id="21ce1-125">The CLR has already been initialized.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21ce1-126">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="21ce1-126">Remarks</span></span>  
 <span data-ttu-id="21ce1-127">Çağırmalısınız `SetHostControl` çağırmadan önce CLR, diğer bir deyişle, başlatılmadan önce [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) veya herhangi birini kullanan [meta veri arabirimleri](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-127">You must call `SetHostControl` before the CLR is initialized, that is, before you call [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) or use any of the [Metadata Interfaces](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md).</span></span> <span data-ttu-id="21ce1-128">Sizi aramasını önerilir `SetHostControl` çağırdıktan hemen sonra [CorBindToCurrentRuntime işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) veya [CorBindToRuntimeEx işlevi](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-128">It is recommended that you call `SetHostControl` immediately after calling [CorBindToCurrentRuntime Function](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md) or [CorBindToRuntimeEx Function](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21ce1-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="21ce1-129">Requirements</span></span>  
 <span data-ttu-id="21ce1-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21ce1-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21ce1-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="21ce1-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21ce1-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="21ce1-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21ce1-133">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21ce1-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ce1-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="21ce1-134">See Also</span></span>  
 [<span data-ttu-id="21ce1-135">Iclrruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="21ce1-135">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="21ce1-136">Ihostcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="21ce1-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
