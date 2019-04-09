---
title: ICLRRuntimeHost::ExecuteApplication Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteApplication
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteApplication
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteApplication method [.NET Framework hosting]
- ExecuteApplication method [.NET Framework hosting]
ms.assetid: 5f28cc4e-7176-4e00-aa1f-58ae6ee52fe4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8ce7e9ff4041abd1e89330bd3a565b755875d3b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194233"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="12dd4-102">ICLRRuntimeHost::ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12dd4-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="12dd4-103">ClickOnce dağıtım senaryolarında bildirim tabanlı yeni bir etki alanı etkinleştirilmesi için uygulamayı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12dd4-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="12dd4-104">Bu senaryolar hakkında daha fazla bilgi için bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="12dd4-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12dd4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="12dd4-105">Syntax</span></span>  
  
```  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12dd4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="12dd4-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="12dd4-107">[in] İçin tanımlandığı gibi uygulamanın tam adını <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="12dd4-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="12dd4-108">[in] Dize içindeki sayısı `ppwzManifestPaths` dizisi.</span><span class="sxs-lookup"><span data-stu-id="12dd4-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="12dd4-109">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="12dd4-109">[in] Optional.</span></span> <span data-ttu-id="12dd4-110">Uygulama için bildirim yolları içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="12dd4-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="12dd4-111">[in] Dize içindeki sayısı `ppwzActivationData` dizisi.</span><span class="sxs-lookup"><span data-stu-id="12dd4-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="12dd4-112">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="12dd4-112">[in] Optional.</span></span> <span data-ttu-id="12dd4-113">Web üzerinden dağıtılan uygulamalar için URL sorgu dizesi kısmı gibi uygulamanın etkinleştirme verileri içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="12dd4-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="12dd4-114">[out] Uygulamanın giriş noktasından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="12dd4-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="12dd4-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="12dd4-115">Return Value</span></span>  
  
|<span data-ttu-id="12dd4-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="12dd4-116">HRESULT</span></span>|<span data-ttu-id="12dd4-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="12dd4-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="12dd4-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="12dd4-118">S_OK</span></span>|`ExecuteApplication` <span data-ttu-id="12dd4-119">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="12dd4-119">returned successfully.</span></span>|  
|<span data-ttu-id="12dd4-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="12dd4-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="12dd4-121">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="12dd4-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="12dd4-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="12dd4-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="12dd4-123">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="12dd4-123">The call timed out.</span></span>|  
|<span data-ttu-id="12dd4-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="12dd4-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="12dd4-125">Arayan bir kilide sahip değil.</span><span class="sxs-lookup"><span data-stu-id="12dd4-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="12dd4-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="12dd4-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="12dd4-127">Bir olay engellenen bir iş parçacığı iptal edildi veya fiber üzerinde bekleme süresi.</span><span class="sxs-lookup"><span data-stu-id="12dd4-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="12dd4-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="12dd4-128">E_FAIL</span></span>|<span data-ttu-id="12dd4-129">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="12dd4-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="12dd4-130">CLR, artık bir yöntem E_FAIL döndürürse, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="12dd4-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="12dd4-131">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="12dd4-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12dd4-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="12dd4-132">Remarks</span></span>  
 `ExecuteApplication` <span data-ttu-id="12dd4-133">Yeni oluşturulan uygulama etki alanındaki ClickOnce uygulamaları etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="12dd4-133">is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="12dd4-134">`pReturnValue` Çıkış parametresi uygulama tarafından döndürülen değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="12dd4-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="12dd4-135">Null değeri sağlarsanız `pReturnValue`, `ExecuteApplication` başarısız olmaz, ancak bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="12dd4-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="12dd4-136">Çağırmayın [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce `ExecuteApplication` bildirim tabanlı bir uygulamayı etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="12dd4-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="12dd4-137">Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="12dd4-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12dd4-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="12dd4-138">Requirements</span></span>  
 <span data-ttu-id="12dd4-139">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12dd4-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12dd4-140">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="12dd4-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="12dd4-141">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="12dd4-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="12dd4-142">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="12dd4-142">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="12dd4-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="12dd4-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="12dd4-144">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="12dd4-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
- [<span data-ttu-id="12dd4-145">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="12dd4-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="12dd4-146">İzlenecek yol: API tasarımcıyı kullanarak ClickOnce dağıtımı ile isteğe bağlı derlemeleri indirme</span><span class="sxs-lookup"><span data-stu-id="12dd4-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
