---
description: ': ICLRRuntimeHost:: ExecuteApplication Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 1511cc3dcf05c3f2243f4080143789e456c39167
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99688981"
---
# <a name="iclrruntimehostexecuteapplication-method"></a><span data-ttu-id="45cab-103">ICLRRuntimeHost::ExecuteApplication Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cab-103">ICLRRuntimeHost::ExecuteApplication Method</span></span>

<span data-ttu-id="45cab-104">Yeni bir etki alanında etkinleştirilecek uygulamayı belirtmek için bildirim tabanlı ClickOnce dağıtım senaryolarında kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45cab-104">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span> <span data-ttu-id="45cab-105">Bu senaryolar hakkında daha fazla bilgi için bkz. [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span><span class="sxs-lookup"><span data-stu-id="45cab-105">For more information about these scenarios, see [ClickOnce Security and Deployment](/visualstudio/deployment/clickonce-security-and-deployment).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45cab-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="45cab-106">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="45cab-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="45cab-107">Parameters</span></span>  

 `pwzAppFullName`  
 <span data-ttu-id="45cab-108">'ndaki Uygulamanın tanımlandığı şekliyle tam adı <xref:System.ApplicationIdentity> .</span><span class="sxs-lookup"><span data-stu-id="45cab-108">[in] The full name of the application, as defined for <xref:System.ApplicationIdentity>.</span></span>  
  
 `dwManifestPaths`  
 <span data-ttu-id="45cab-109">'ndaki Dizide bulunan dizelerin sayısı `ppwzManifestPaths` .</span><span class="sxs-lookup"><span data-stu-id="45cab-109">[in] The number of strings contained in the `ppwzManifestPaths` array.</span></span>  
  
 `ppwzManifestPaths`  
 <span data-ttu-id="45cab-110">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="45cab-110">[in] Optional.</span></span> <span data-ttu-id="45cab-111">Uygulamanın bildirim yollarını içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="45cab-111">A string array that contains manifest paths for the application.</span></span>  
  
 `dwActivationData`  
 <span data-ttu-id="45cab-112">'ndaki Dizide bulunan dizelerin sayısı `ppwzActivationData` .</span><span class="sxs-lookup"><span data-stu-id="45cab-112">[in] The number of strings contained in the `ppwzActivationData` array.</span></span>  
  
 `ppwzActivationData`  
 <span data-ttu-id="45cab-113">'ndaki Seçim.</span><span class="sxs-lookup"><span data-stu-id="45cab-113">[in] Optional.</span></span> <span data-ttu-id="45cab-114">Web üzerinde dağıtılan uygulamalar için URL 'nin sorgu dizesi kısmı gibi uygulamanın etkinleştirme verilerini içeren bir dize dizisi.</span><span class="sxs-lookup"><span data-stu-id="45cab-114">A string array that contains the application's activation data, such as the query string portion of the URL for applications deployed over the Web.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="45cab-115">dışı Uygulamanın giriş noktasından döndürülen değer.</span><span class="sxs-lookup"><span data-stu-id="45cab-115">[out] The value returned from the entry point of the application.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45cab-116">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="45cab-116">Return Value</span></span>  
  
|<span data-ttu-id="45cab-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="45cab-117">HRESULT</span></span>|<span data-ttu-id="45cab-118">Description</span><span class="sxs-lookup"><span data-stu-id="45cab-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="45cab-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="45cab-119">S_OK</span></span>|<span data-ttu-id="45cab-120">`ExecuteApplication` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="45cab-120">`ExecuteApplication` returned successfully.</span></span>|  
|<span data-ttu-id="45cab-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="45cab-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="45cab-122">Ortak dil çalışma zamanı (CLR) bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramayacağı veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="45cab-122">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="45cab-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="45cab-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="45cab-124">Çağrı zaman aşımına uğradı.</span><span class="sxs-lookup"><span data-stu-id="45cab-124">The call timed out.</span></span>|  
|<span data-ttu-id="45cab-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="45cab-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="45cab-126">Çağıranın kilidi yoktur.</span><span class="sxs-lookup"><span data-stu-id="45cab-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="45cab-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="45cab-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="45cab-128">Engellenen bir iş parçacığı veya fiber üzerinde beklerken bir olay iptal edildi.</span><span class="sxs-lookup"><span data-stu-id="45cab-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="45cab-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="45cab-129">E_FAIL</span></span>|<span data-ttu-id="45cab-130">Bilinmeyen bir çok zararlı hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="45cab-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="45cab-131">Bir yöntem E_FAIL döndürürse, CLR artık işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="45cab-131">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="45cab-132">Barındırma yöntemlerine yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="45cab-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45cab-133">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="45cab-133">Remarks</span></span>  

 <span data-ttu-id="45cab-134">`ExecuteApplication` , yeni oluşturulan bir uygulama etki alanında ClickOnce uygulamalarını etkinleştirmek için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="45cab-134">`ExecuteApplication` is used to activate ClickOnce applications in a newly created application domain.</span></span>  
  
 <span data-ttu-id="45cab-135">`pReturnValue`Output parametresi, uygulama tarafından döndürülen değere ayarlanır.</span><span class="sxs-lookup"><span data-stu-id="45cab-135">The `pReturnValue` output parameter is set to the value returned by the application.</span></span> <span data-ttu-id="45cab-136">İçin null değeri sağlarsanız, `pReturnValue` `ExecuteApplication` başarısız olmaz, ancak bir değer döndürmez.</span><span class="sxs-lookup"><span data-stu-id="45cab-136">If you supply a value of null for `pReturnValue`, `ExecuteApplication` does not fail, but it does not return a value.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="45cab-137">Bildirim tabanlı bir uygulamayı etkinleştirmek için yöntemini çağırmadan önce [Start yöntemi](iclrruntimehost-start-method.md) yöntemini çağırmayın `ExecuteApplication` .</span><span class="sxs-lookup"><span data-stu-id="45cab-137">Do not call the [Start Method](iclrruntimehost-start-method.md) method before calling the `ExecuteApplication` method to activate a manifest-based application.</span></span> <span data-ttu-id="45cab-138">`Start`Yöntemi ilk kez çağrılırsa `ExecuteApplication` Yöntem çağrısı başarısız olur.</span><span class="sxs-lookup"><span data-stu-id="45cab-138">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45cab-139">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="45cab-139">Requirements</span></span>  

 <span data-ttu-id="45cab-140">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45cab-140">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45cab-141">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="45cab-141">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="45cab-142">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="45cab-142">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="45cab-143">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="45cab-143">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cab-144">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="45cab-144">See also</span></span>

- <xref:System.ActivationContext>
- <xref:System.AppDomainManager>
- <xref:System.ApplicationIdentity>
- [<span data-ttu-id="45cab-145">ICLRRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="45cab-145">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
- [<span data-ttu-id="45cab-146">SetAppDomainManager Yöntemi</span><span class="sxs-lookup"><span data-stu-id="45cab-146">SetAppDomainManager Method</span></span>](ihostcontrol-setappdomainmanager-method.md)
- [<span data-ttu-id="45cab-147">İzlenecek yol: Tasarımcıyı Kullanarak ClickOnce Dağıtım API'si ile İsteğe Bağlı Derlemeleri İndirme</span><span class="sxs-lookup"><span data-stu-id="45cab-147">Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer</span></span>](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer)
