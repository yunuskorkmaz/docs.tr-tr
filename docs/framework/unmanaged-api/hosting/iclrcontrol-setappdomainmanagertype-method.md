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
ms.workload: dotnet
ms.openlocfilehash: bbddefa4211d63f012bce3532d7133b59c4ee1b1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="0f898-102">ICLRControl::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f898-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="0f898-103">Öğesinden türetilen bir tür ayarlar <xref:System.AppDomainManager> uygulama etki alanı yöneticileri için türü olarak.</span><span class="sxs-lookup"><span data-stu-id="0f898-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f898-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f898-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f898-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f898-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="0f898-106">[in] İçinde istenen tür türetilen derlemenin adını <xref:System.AppDomainManager> uygulanır.</span><span class="sxs-lookup"><span data-stu-id="0f898-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="0f898-107">[in] Uygulanan türünün adı `pwzAppDomainManagerAssembly` özelliklerini uygulayan parametresi <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="0f898-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f898-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f898-108">Return Value</span></span>  
  
|<span data-ttu-id="0f898-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f898-109">HRESULT</span></span>|<span data-ttu-id="0f898-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f898-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f898-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f898-111">S_OK</span></span>|<span data-ttu-id="0f898-112">Yöntem başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0f898-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="0f898-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f898-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f898-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0f898-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f898-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0f898-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0f898-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="0f898-116">The call timed out.</span></span>|  
|<span data-ttu-id="0f898-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0f898-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0f898-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="0f898-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0f898-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0f898-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0f898-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="0f898-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0f898-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f898-121">E_FAIL</span></span>|<span data-ttu-id="0f898-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0f898-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f898-123">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0f898-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f898-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f898-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f898-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f898-125">Requirements</span></span>  
 <span data-ttu-id="0f898-126">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f898-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f898-127">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f898-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f898-128">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0f898-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f898-129">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f898-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f898-130">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f898-130">See Also</span></span>  
 [<span data-ttu-id="0f898-131">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f898-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="0f898-132">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f898-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
