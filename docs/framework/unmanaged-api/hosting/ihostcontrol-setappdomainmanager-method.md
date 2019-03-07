---
title: IHostControl::SetAppDomainManager Yöntemi
ms.date: 03/30/2017
api_name:
- IHostControl.SetAppDomainManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostControl::SetAppDomainManager
helpviewer_keywords:
- IHostControl::SetAppDomainManager method [.NET Framework hosting]
- SetAppDomainManager method [.NET Framework hosting]
ms.assetid: 6562bbe7-0d67-4c50-a958-3a18cf680375
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 83461f89be9a16305da2732536dcc6847b45027d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482567"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="a1f68-102">IHostControl::SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1f68-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="a1f68-103">Konak, bir uygulama etki alanı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="a1f68-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f68-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1f68-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1f68-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="a1f68-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="a1f68-106">[in] Seçili sayısal tanımlayıcı <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a1f68-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="a1f68-107">[in] Bir işaretçi <xref:System.AppDomainManager> konak olarak uygulayan nesne `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="a1f68-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a1f68-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="a1f68-108">Return Value</span></span>  
  
|<span data-ttu-id="a1f68-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a1f68-109">HRESULT</span></span>|<span data-ttu-id="a1f68-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="a1f68-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a1f68-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a1f68-111">S_OK</span></span>|<span data-ttu-id="a1f68-112">`SetAppDomainManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="a1f68-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="a1f68-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a1f68-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a1f68-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="a1f68-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a1f68-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a1f68-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a1f68-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="a1f68-116">The call timed out.</span></span>|  
|<span data-ttu-id="a1f68-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a1f68-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a1f68-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="a1f68-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a1f68-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a1f68-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a1f68-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="a1f68-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a1f68-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a1f68-121">E_FAIL</span></span>|<span data-ttu-id="a1f68-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="a1f68-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a1f68-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="a1f68-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a1f68-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="a1f68-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1f68-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1f68-125">Remarks</span></span>  
 <span data-ttu-id="a1f68-126"><xref:System.AppDomainManager> Yönetilen koda bootstrap ve oluşturulması ve her birinin ayarlarını denetlemek için bir mekanizma ile ana bilgisayarının sağladığı <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a1f68-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="a1f68-127"><xref:System.AppDomainManager> Her birinde yüklü olduğu <xref:System.AppDomain> olduğunda, <xref:System.AppDomain> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="a1f68-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="a1f68-128">Seçerse, CLR konak uygulama etki alanı değerini ayarlayarak oluşturulduğunu bildirir `pUnkAppDomainManager` parametresi.</span><span class="sxs-lookup"><span data-stu-id="a1f68-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="a1f68-129">Uygulamaya `SetAppDomainManager` yöntemi, konak ayarlayabilir derleme adı ve türü için uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="a1f68-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1f68-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1f68-130">Requirements</span></span>  
 <span data-ttu-id="a1f68-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f68-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f68-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1f68-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1f68-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a1f68-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1f68-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1f68-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1f68-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1f68-135">See also</span></span>
- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="a1f68-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1f68-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
