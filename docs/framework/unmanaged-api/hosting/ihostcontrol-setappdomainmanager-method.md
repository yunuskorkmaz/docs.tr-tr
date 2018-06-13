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
ms.openlocfilehash: bb63f1e9d2b30ce764521aa68fbafe0407cbe922
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33441880"
---
# <a name="ihostcontrolsetappdomainmanager-method"></a><span data-ttu-id="e167f-102">IHostControl::SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e167f-102">IHostControl::SetAppDomainManager Method</span></span>
<span data-ttu-id="e167f-103">Ana uygulama etki alanı oluşturulduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="e167f-103">Notifies the host that an application domain has been created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e167f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e167f-104">Syntax</span></span>  
  
```  
HRESULT SetAppDomainManager (  
    [in] DWORD     dwAppDomainID,  
    [in] IUnknown* pUnkAppDomainManager  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e167f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e167f-105">Parameters</span></span>  
 `dwAppDomainID`  
 <span data-ttu-id="e167f-106">[in] Seçili sayısal tanımlayıcı <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e167f-106">[in] The numeric identifier of the selected <xref:System.AppDomain>.</span></span>  
  
 `pUnkAppDomainManager`  
 <span data-ttu-id="e167f-107">[in] Bir işaretçi <xref:System.AppDomainManager> olarak ana bilgisayar uygulayan nesne `IUnknown`.</span><span class="sxs-lookup"><span data-stu-id="e167f-107">[in] A pointer to the <xref:System.AppDomainManager> object that the host implements as `IUnknown`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e167f-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e167f-108">Return Value</span></span>  
  
|<span data-ttu-id="e167f-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e167f-109">HRESULT</span></span>|<span data-ttu-id="e167f-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e167f-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e167f-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e167f-111">S_OK</span></span>|<span data-ttu-id="e167f-112">`SetAppDomainManager` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e167f-112">`SetAppDomainManager` returned successfully.</span></span>|  
|<span data-ttu-id="e167f-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e167f-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e167f-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="e167f-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e167f-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="e167f-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="e167f-116">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="e167f-116">The call timed out.</span></span>|  
|<span data-ttu-id="e167f-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="e167f-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="e167f-118">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="e167f-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="e167f-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="e167f-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="e167f-120">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="e167f-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="e167f-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e167f-121">E_FAIL</span></span>|<span data-ttu-id="e167f-122">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e167f-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e167f-123">Bir yöntem E_FAIL döndüğünde, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e167f-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e167f-124">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e167f-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e167f-125">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e167f-125">Remarks</span></span>  
 <span data-ttu-id="e167f-126"><xref:System.AppDomainManager> Yönetilen koda bootstrap ve oluşturulması ve her birinin ayarlarını denetlemek için bir mekanizma ile ana bilgisayarının sağladığı <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="e167f-126">The <xref:System.AppDomainManager> provides the host with a mechanism to bootstrap into managed code and to control the creation and settings of each <xref:System.AppDomain>.</span></span> <span data-ttu-id="e167f-127"><xref:System.AppDomainManager> Her yüklenir <xref:System.AppDomain> olduğunda, <xref:System.AppDomain> oluşturulur.</span><span class="sxs-lookup"><span data-stu-id="e167f-127">The <xref:System.AppDomainManager> is loaded into each <xref:System.AppDomain> when that <xref:System.AppDomain> is created.</span></span> <span data-ttu-id="e167f-128">Seçerse, CLR ana uygulama etki alanı değerini ayarlayarak oluşturuldu bildirir `pUnkAppDomainManager` parametresi.</span><span class="sxs-lookup"><span data-stu-id="e167f-128">If it chooses, the CLR notifies the host that the application domain has been created by setting the value of the `pUnkAppDomainManager` parameter.</span></span>  
  
 <span data-ttu-id="e167f-129">Uygulamaya `SetAppDomainManager` yöntemi, ana bilgisayar ayarlayabilirsiniz derleme adı ve türü için uygulama etki alanı yöneticisi.</span><span class="sxs-lookup"><span data-stu-id="e167f-129">In its implementation of the `SetAppDomainManager` method, the host can set the assembly name and type for the application domain manager.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e167f-130">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e167f-130">Requirements</span></span>  
 <span data-ttu-id="e167f-131">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e167f-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e167f-132">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e167f-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e167f-133">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e167f-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e167f-134">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e167f-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e167f-135">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e167f-135">See Also</span></span>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainManager>  
 [<span data-ttu-id="e167f-136">IHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e167f-136">IHostControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)
