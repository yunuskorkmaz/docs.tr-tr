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
ms.openlocfilehash: ef043dd2308c4b76e975bd2ad1f68725579e8fc9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728920"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="08d94-102">ICLRRuntimeHost::ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08d94-102">ICLRRuntimeHost::ExecuteApplication Method</span></span>

<span data-ttu-id="08d94-103">Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08d94-103">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="08d94-104">Bu senaryolar hakkında daha fazla bilgi için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="08d94-104">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08d94-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="08d94-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteApplication(  
    [in] LPCWSTR   pwzAppFullName,  
    [in] DWORD     dwManifestPaths,  
    [in] LPCWSTR   *ppwzManifestPaths,  
    [in] DWORD     dwActivationData,  
    [in] LPCWSTR   *ppwzActivationData,  
    [out] int      *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08d94-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="08d94-106">Parameters</span></span>  

 `pwzAppFullName`  
 <span data-ttu-id="08d94-107">'ndaki Uygulamanın tanımlandığı şekliyle tam adı <xref:System.ApplicationIdentity> .</span><span class="sxs-lookup"><span data-stu-id="08d94-107">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="08d94-108">'ndaki Dizide bulunan dizelerin sayısı `ppwzManifestPaths` .</span><span class="sxs-lookup"><span data-stu-id="08d94-108">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="08d94-109">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="08d94-109">[in] Optional.</span></span> <span data-ttu-id="08d94-110">Uygulamanın bildirim yollarını içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="08d94-110">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="08d94-111">'ndaki Dizide bulunan dizelerin sayısı `ppwzActivationData` .</span><span class="sxs-lookup"><span data-stu-id="08d94-111">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="08d94-112">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="08d94-112">[in] Optional.</span></span> <span data-ttu-id="08d94-113">Web üzerinde dağıtılan uygulamalar için URL 'nin sorgu dizesi kısmı gibi uygulamanın etkinleştirme verilerini içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="08d94-113">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="08d94-114">dışı Uygulamanın giriş noktasından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="08d94-114">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08d94-115">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="08d94-115">Return Value</span></span>  
  
|<span data-ttu-id="08d94-116">HRESULT</span><span class="sxs-lookup"><span data-stu-id="08d94-116">HRESULT</span></span>|<span data-ttu-id="08d94-117">Açıklama</span><span class="sxs-lookup"><span data-stu-id="08d94-117">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="08d94-118">S_OK</span><span class="sxs-lookup"><span data-stu-id="08d94-118">S_OK</span></span>|<span data-ttu-id="08d94-119">`ExecuteApplication` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="08d94-119">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="08d94-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="08d94-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="08d94-121">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="08d94-121">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="08d94-122">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="08d94-122">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="08d94-123">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="08d94-123">The call timed out.</span></span>|  
|<span data-ttu-id="08d94-124">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="08d94-124">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="08d94-125">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="08d94-125">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="08d94-126">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="08d94-126">HOST_E_ABANDONED</span></span>|<span data-ttu-id="08d94-127">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="08d94-127">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="08d94-128">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="08d94-128">E_FAIL</span></span>|<span data-ttu-id="08d94-129">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="08d94-129">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="08d94-130">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="08d94-130">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="08d94-131">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="08d94-131">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08d94-132">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="08d94-132">Remarks</span></span>  

 <span data-ttu-id="08d94-133">`ExecuteApplication` , yeni oluşturulan bir uygulama etki alanında ClickOnce uygulamalarını etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="08d94-133">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="08d94-134">`pReturnValue`Output parametresi, uygulama tarafından döndürülen değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="08d94-134">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="08d94-135">İçin null değeri sağlarsanız, `pReturnValue` `ExecuteApplication` başarısız olmaz, ancak bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="08d94-135">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="08d94-136">Bildirim tabanlı bir uygulamayı etkinleştirmek için yöntemini çağırmadan önce [Start yöntemi](iclrruntimehost-start-method.md) yöntemini çağırmayın `ExecuteApplication` .</span><span class="sxs-lookup"><span data-stu-id="08d94-136">Do not call the [Start Method](iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="08d94-137">`Start`Yöntemi ilk kez çağrılırsa `ExecuteApplication` Yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="08d94-137">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08d94-138">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="08d94-138">Requirements</span></span>  

 <span data-ttu-id="08d94-139">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08d94-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08d94-140">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="08d94-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="08d94-141">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="08d94-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="08d94-142">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08d94-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08d94-143">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="08d94-143">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="08d94-144">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="08d94-144">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="08d94-145">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="08d94-145">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="08d94-146">İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme</span><span class="sxs-lookup"><span data-stu-id="08d94-146">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
