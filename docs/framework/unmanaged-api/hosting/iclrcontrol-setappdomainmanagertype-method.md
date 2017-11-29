---
title: "ICLRControl::SetAppDomainManagerType Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRControl.SetAppDomainManagerType
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6632417cb0cfe17d7bde16ecf47ae1c001f43f2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="891cb-102">ICLRControl::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="891cb-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="891cb-103">Öğesinden türetilen bir tür ayarlar <xref:System.AppDomainManager> uygulama etki alanı yöneticileri için türü olarak.</span><span class="sxs-lookup"><span data-stu-id="891cb-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="891cb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="891cb-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="891cb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="891cb-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="891cb-106">[in] İçinde istenen tür türetilen derlemenin adını <xref:System.AppDomainManager> uygulanır.</span><span class="sxs-lookup"><span data-stu-id="891cb-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="891cb-107">[in] Uygulanan türünün adı `pwzAppDomainManagerAssembly` özelliklerini uygulayan parametresi <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="891cb-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="891cb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="891cb-108">Return Value</span></span>  
  
|<span data-ttu-id="891cb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="891cb-109">HRESULT</span></span>|<span data-ttu-id="891cb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="891cb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="891cb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="891cb-111">S_OK</span></span>|<span data-ttu-id="891cb-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="891cb-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="891cb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="891cb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="891cb-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="891cb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="891cb-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="891cb-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="891cb-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="891cb-116">The call timed out.</span></span>|  
|<span data-ttu-id="891cb-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="891cb-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="891cb-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="891cb-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="891cb-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="891cb-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="891cb-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="891cb-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="891cb-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="891cb-121">E_FAIL</span></span>|<span data-ttu-id="891cb-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="891cb-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="891cb-123">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="891cb-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="891cb-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="891cb-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="891cb-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="891cb-125">Requirements</span></span>  
 <span data-ttu-id="891cb-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="891cb-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="891cb-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="891cb-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="891cb-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="891cb-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="891cb-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="891cb-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="891cb-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="891cb-130">See Also</span></span>  
 [<span data-ttu-id="891cb-131">Iclrcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="891cb-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="891cb-132">Ihostcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="891cb-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
