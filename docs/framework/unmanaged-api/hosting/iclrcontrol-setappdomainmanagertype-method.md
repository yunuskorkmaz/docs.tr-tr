---
title: ICLRControl::SetAppDomainManagerType Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRControl.SetAppDomainManagerType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::SetAppDomainManagerType
helpviewer_keywords:
- SetAppDomainManagerType method, ICLRControl interface [.NET Framework hosting]
- ICLRControl::SetAppDomainManagerType method [.NET Framework hosting]
ms.assetid: ec57828b-2aad-496d-a35a-e45d4bd7fe77
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d79d3651bb949899681eac2e7d2ac49d9233ccc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531787"
---
# <a name="iclrcontrolsetappdomainmanagertype-method"></a><span data-ttu-id="e01ac-102">ICLRControl::SetAppDomainManagerType Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e01ac-102">ICLRControl::SetAppDomainManagerType Method</span></span>
<span data-ttu-id="e01ac-103">Türetilen bir türü ayarlar <xref:System.AppDomainManager> uygulama etki alanı yöneticileri için türü.</span><span class="sxs-lookup"><span data-stu-id="e01ac-103">Sets a type derived from <xref:System.AppDomainManager> as the type for application domain managers.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e01ac-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e01ac-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManagerType (  
    [in] LPCWSTR pwzAppDomainManagerAssembly,  
    [in] LPCWSTR pwzAppDomainManagerType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e01ac-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e01ac-105">Parameters</span></span>  
 `pwzAppDomainManagerAssembly`  
 <span data-ttu-id="e01ac-106">[in] İstenen türü türetilen, derlemenin adı <xref:System.AppDomainManager> uygulanır.</span><span class="sxs-lookup"><span data-stu-id="e01ac-106">[in] The name of the assembly in which the requested type derived from <xref:System.AppDomainManager> is implemented.</span></span>  
  
 `pwzAppDomainManagerType`  
 <span data-ttu-id="e01ac-107">[in] Uygulanan türünün adı `pwzAppDomainManagerAssembly` yeteneklerini uygulayan parametresi <xref:System.AppDomainManager>.</span><span class="sxs-lookup"><span data-stu-id="e01ac-107">[in] The name of the type implemented in the `pwzAppDomainManagerAssembly` parameter that implements the capabilities of <xref:System.AppDomainManager>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e01ac-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e01ac-108">Return Value</span></span>  
  
|<span data-ttu-id="e01ac-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e01ac-109">HRESULT</span></span>|<span data-ttu-id="e01ac-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e01ac-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e01ac-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e01ac-111">S_OK</span></span>|<span data-ttu-id="e01ac-112">Yöntemi başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e01ac-112">The method returned successfully.</span></span>|  
|<span data-ttu-id="e01ac-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e01ac-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e01ac-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e01ac-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e01ac-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e01ac-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e01ac-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e01ac-116">The call timed out.</span></span>|  
|<span data-ttu-id="e01ac-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e01ac-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e01ac-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="e01ac-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e01ac-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e01ac-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e01ac-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="e01ac-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e01ac-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e01ac-121">E_FAIL</span></span>|<span data-ttu-id="e01ac-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e01ac-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e01ac-123">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e01ac-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e01ac-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e01ac-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e01ac-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e01ac-125">Requirements</span></span>  
 <span data-ttu-id="e01ac-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e01ac-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e01ac-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e01ac-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e01ac-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e01ac-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e01ac-129">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e01ac-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01ac-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e01ac-130">See also</span></span>
- [<span data-ttu-id="e01ac-131">ICLRControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e01ac-131">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="e01ac-132">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e01ac-132">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
