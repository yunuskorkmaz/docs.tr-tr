---
title: "ICLRRuntimeHost::ExecuteApplication Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b765f020bd15fa94fb18a6fd7d81cf66c534639
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="2d607-102">ICLRRuntimeHost::ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d607-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>
<span data-ttu-id="2d607-103">ClickOnce dağıtım senaryolarında bildirimi tabanlı yeni bir etki alanına etkinleştirilmesi için uygulamayı belirtmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d607-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="2d607-104">Bu senaryolar hakkında daha fazla bilgi için bkz: [ClickOnce güvenliği ve dağıtımı](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="2d607-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d607-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d607-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="2d607-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2d607-106">Parameters</span></span>  
 `pwzAppFullName`  
 <span data-ttu-id="2d607-107">[in] İçin tanımlanan uygulamasının tam adı <xref:System.ApplicationIdentity>.</span><span class="sxs-lookup"><span data-stu-id="2d607-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="2d607-108">[in] İçinde yer alan dizeleri sayısı `ppwzManifestPaths` dizi.</span><span class="sxs-lookup"><span data-stu-id="2d607-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="2d607-109">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2d607-109">[in] Optional.</span></span> <span data-ttu-id="2d607-110">Uygulama için bildirim yolları içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="2d607-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="2d607-111">[in] İçinde yer alan dizeleri sayısı `ppwzActivationData` dizi.</span><span class="sxs-lookup"><span data-stu-id="2d607-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="2d607-112">[in] İsteğe bağlı.</span><span class="sxs-lookup"><span data-stu-id="2d607-112">[in] Optional.</span></span> <span data-ttu-id="2d607-113">Web üzerinden dağıtılan uygulamalar için URL sorgu dizesi bölümünü gibi uygulamanın etkinleştirme verileri içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="2d607-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="2d607-114">[out] Uygulama giriş noktasından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="2d607-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2d607-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2d607-115">Return Value</span></span>  
  
|<span data-ttu-id="2d607-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2d607-116">HRESULT</span></span>|<span data-ttu-id="2d607-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2d607-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2d607-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="2d607-118">S_OK</span></span>|<span data-ttu-id="2d607-119">`ExecuteApplication`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="2d607-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="2d607-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2d607-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2d607-121">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2d607-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2d607-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2d607-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2d607-123">Arama zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="2d607-123">The call timed out.</span></span>|  
|<span data-ttu-id="2d607-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2d607-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2d607-125">Arayan kilidi kendisine ait değil.</span><span class="sxs-lookup"><span data-stu-id="2d607-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2d607-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2d607-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2d607-127">Bir olay engellenmiş iş parçacığı sırasında iptal edildi veya fiber üzerinde beklediği.</span><span class="sxs-lookup"><span data-stu-id="2d607-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2d607-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2d607-128">E_FAIL</span></span>|<span data-ttu-id="2d607-129">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2d607-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2d607-130">Bir yöntem E_FAIL döndürürse, CLR artık işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2d607-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2d607-131">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2d607-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d607-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d607-132">Remarks</span></span>  
 <span data-ttu-id="2d607-133">`ExecuteApplication`ClickOnce uygulamaları yeni oluşturulan uygulama etki alanındaki etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="2d607-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="2d607-134">`pReturnValue` Çıktı parametresi, uygulama tarafından döndürülen değer ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="2d607-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="2d607-135">Null değeri sağlarsanız `pReturnValue`, `ExecuteApplication` başarısız değil, ancak bir değer döndürmüyor.</span><span class="sxs-lookup"><span data-stu-id="2d607-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="2d607-136">Çağırmayın [Start yöntemi](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) yöntemi çağırmadan önce `ExecuteApplication` bildirimi tabanlı bir uygulama etkinleştirmek için yöntemi.</span><span class="sxs-lookup"><span data-stu-id="2d607-136">Do not call the [Start Method](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="2d607-137">Varsa `Start` yöntemi önce çağrılır `ExecuteApplication` yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="2d607-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d607-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d607-138">Requirements</span></span>  
 <span data-ttu-id="2d607-139">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d607-139">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d607-140">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d607-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d607-141">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2d607-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d607-142">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d607-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d607-143">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d607-143">See Also</span></span>  
 <xref:System.ActivationContext>  
 <xref:System.AppDomainManager>  
 <xref:System.ApplicationIdentity>  
 [<span data-ttu-id="2d607-144">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d607-144">ICLRRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 [<span data-ttu-id="2d607-145">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d607-145">SetAppDomainManager Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-setappdomainmanager-method.md)  
 [<span data-ttu-id="2d607-146">İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme</span><span class="sxs-lookup"><span data-stu-id="2d607-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
