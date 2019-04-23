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
ms.openlocfilehash: 118e75cb28a4e474427f35f4516ec41850ebe99f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150871"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="c7e0c-102">IHostControl::SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7e0c-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="c7e0c-103">Konak, bir uygulama etki alanı oluşturulduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7e0c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7e0c-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7e0c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7e0c-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="c7e0c-106">[in] Seçili sayısal tanımlayıcı <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="c7e0c-107">[in] Bir işaretçi <xref:System.AppDomainManager> konak olarak uygulayan nesne `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7e0c-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7e0c-108">Return Value</span></span>  
  
|<span data-ttu-id="c7e0c-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7e0c-109">HRESULT</span></span>|<span data-ttu-id="c7e0c-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7e0c-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7e0c-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7e0c-111">S_OK</span></span>|<span data-ttu-id="c7e0c-112">`SetAppDomainManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="c7e0c-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7e0c-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7e0c-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="c7e0c-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="c7e0c-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="c7e0c-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-116">The call timed out.</span></span>|  
|<span data-ttu-id="c7e0c-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="c7e0c-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="c7e0c-118">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="c7e0c-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="c7e0c-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="c7e0c-120">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="c7e0c-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c7e0c-121">E_FAIL</span></span>|<span data-ttu-id="c7e0c-122">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="c7e0c-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="c7e0c-124">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7e0c-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7e0c-125">Remarks</span></span>  
 <span data-ttu-id="c7e0c-126"><xref:System.AppDomainManager> Yönetilen koda bootstrap ve oluşturulması ve her birinin ayarlarını denetlemek için bir mekanizma ile ana bilgisayarının sağladığı <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="c7e0c-127"><xref:System.AppDomainManager> Her birinde yüklü olduğu <xref:System.AppDomain> olduğunda, <xref:System.AppDomain> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="c7e0c-128">Seçerse, CLR konak uygulama etki alanı değerini ayarlayarak oluşturulduğunu bildirir `pUnkAppDomainManager` parametresi.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="c7e0c-129">Uygulamaya `SetAppDomainManager` yöntemi, konak ayarlayabilir derleme adı ve türü için uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7e0c-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7e0c-130">Requirements</span></span>  
 <span data-ttu-id="c7e0c-131">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7e0c-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7e0c-132">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c7e0c-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7e0c-133">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c7e0c-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7e0c-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7e0c-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7e0c-135">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7e0c-135">See also</span></span>

- <xref:System.AppDomain>
- <xref:System.AppDomainManager>
- [<span data-ttu-id="c7e0c-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7e0c-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
