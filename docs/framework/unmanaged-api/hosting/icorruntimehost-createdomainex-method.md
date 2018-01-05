---
title: "ICorRuntimeHost::CreateDomainEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainEx
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2a577e1bd8765c7359e521b007bea943de7a984
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="47032-102">ICorRuntimeHost::CreateDomainEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47032-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="47032-103">Uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="47032-103">Creates an application domain.</span></span> <span data-ttu-id="47032-104">Arayan türünde bir arabirim işaretçisi alır <xref:System._AppDomain>, türünün bir örneği için <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="47032-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="47032-105">Bu yöntem döndürülen ek özelliklerini yapılandırmak için Iappdomainsetup örneği geçirmek arayan sağlar <xref:System._AppDomain> örneği.</span><span class="sxs-lookup"><span data-stu-id="47032-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47032-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="47032-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="47032-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="47032-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="47032-108">[in] Etki alanı için kolay bir ad vermek için kullanılan isteğe bağlı bir parametre.</span><span class="sxs-lookup"><span data-stu-id="47032-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="47032-109">Bu kolay adı etki alanını tanımlamak için hata ayıklayıcıları gibi kullanıcı arabirimleri görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="47032-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="47032-110">[in] Bir isteğe bağlı bir arabirim işaretçisi türü `IAppDomainSetup`, bir çağrı tarafından alınan [Icorruntimehost::createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47032-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="47032-111">[in] İşaretçiler isteğe bağlı bir dizi `IIdentity` bir izin kümesi oluşturmak için Güvenlik İlkesi aracılığıyla eşlenen kanıt temsil örnekleri.</span><span class="sxs-lookup"><span data-stu-id="47032-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="47032-112">Bir `IIdentity` nesne elde edilebilir çağırarak [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="47032-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="47032-113">[out] Arabirim işaretçisi türü <xref:System._AppDomain> örneğine <xref:System.AppDomain?displayProperty=nameWithType> daha fazla etki alanı denetlemek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="47032-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="47032-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="47032-114">Return Value</span></span>  
  
|<span data-ttu-id="47032-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="47032-115">HRESULT</span></span>|<span data-ttu-id="47032-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="47032-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47032-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="47032-117">S_OK</span></span>|<span data-ttu-id="47032-118">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="47032-118">The operation was successful.</span></span>|  
|<span data-ttu-id="47032-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="47032-119">S_FALSE</span></span>|<span data-ttu-id="47032-120">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="47032-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="47032-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="47032-121">E_FAIL</span></span>|<span data-ttu-id="47032-122">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="47032-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="47032-123">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="47032-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="47032-124">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="47032-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="47032-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="47032-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="47032-126">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="47032-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47032-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="47032-127">Remarks</span></span>  
 <span data-ttu-id="47032-128">`CreateDomainEx`yeteneklerini genişletir [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) arayan geçirin sağlayarak bir `IAppDomainSetup` uygulama etki alanını yapılandırmak için özellik değerlerini örneğiyle.</span><span class="sxs-lookup"><span data-stu-id="47032-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47032-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="47032-129">Requirements</span></span>  
 <span data-ttu-id="47032-130">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47032-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47032-131">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="47032-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="47032-132">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="47032-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="47032-133">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="47032-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47032-134">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="47032-134">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="47032-135">CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="47032-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)  
 [<span data-ttu-id="47032-136">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="47032-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
