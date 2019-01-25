---
title: ICorRuntimeHost::CreateDomainEx Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bf8cb9382b2bbf10d02cf564ee51db626d81c6a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650632"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="560d7-102">ICorRuntimeHost::CreateDomainEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="560d7-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="560d7-103">Uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="560d7-103">Creates an application domain.</span></span> <span data-ttu-id="560d7-104">Çağıranın türü bir arabirim işaretçisi alır <xref:System._AppDomain>, türde bir örnek <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="560d7-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="560d7-105">Bu yöntemi çağıran döndürülen ek özellikleri yapılandırmak için Iappdomainsetup örneği geçirilecek sağlar <xref:System._AppDomain> örneği.</span><span class="sxs-lookup"><span data-stu-id="560d7-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="560d7-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="560d7-106">Syntax</span></span>  
  
```  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="560d7-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="560d7-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="560d7-108">[in] Etki alanında kolay bir ad vermek için kullanılan isteğe bağlı bir parametre.</span><span class="sxs-lookup"><span data-stu-id="560d7-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="560d7-109">Bu kolay adı, etki alanını tanımlamak için hata ayıklayıcıları gibi kullanıcı arabirimlerinde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="560d7-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="560d7-110">[in] Bir isteğe bağlı bir arabirim işaretçisi türünde `IAppDomainSetup`, bir çağrı tarafından alınan [Icorruntimehost::createdomainsetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="560d7-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="560d7-111">[in] İsteğe bağlı bir işaretçiler dizisi `IIdentity` kanıt eşlenmiş bir izin kümesi oluşturmak için Güvenlik İlkesi aracılığıyla temsil eden örnekleri.</span><span class="sxs-lookup"><span data-stu-id="560d7-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="560d7-112">Bir `IIdentity` nesnesi elde edilebilir çağırarak [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="560d7-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="560d7-113">[out] Bir arabirim işaretçisi türünde <xref:System._AppDomain> örneğine <xref:System.AppDomain?displayProperty=nameWithType> daha fazla etki alanı kontrol etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="560d7-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="560d7-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="560d7-114">Return Value</span></span>  
  
|<span data-ttu-id="560d7-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="560d7-115">HRESULT</span></span>|<span data-ttu-id="560d7-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="560d7-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="560d7-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="560d7-117">S_OK</span></span>|<span data-ttu-id="560d7-118">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="560d7-118">The operation was successful.</span></span>|  
|<span data-ttu-id="560d7-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="560d7-119">S_FALSE</span></span>|<span data-ttu-id="560d7-120">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="560d7-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="560d7-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="560d7-121">E_FAIL</span></span>|<span data-ttu-id="560d7-122">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="560d7-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="560d7-123">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="560d7-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="560d7-124">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="560d7-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="560d7-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="560d7-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="560d7-126">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="560d7-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="560d7-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="560d7-127">Remarks</span></span>  
 <span data-ttu-id="560d7-128">`CreateDomainEx` yeteneklerini genişletir [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) geçirin için çağıranı sağlayarak bir `IAppDomainSetup` uygulama etki alanı yapılandırma için özellik değerlerini örneği.</span><span class="sxs-lookup"><span data-stu-id="560d7-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="560d7-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="560d7-129">Requirements</span></span>  
 <span data-ttu-id="560d7-130">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="560d7-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="560d7-131">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="560d7-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="560d7-132">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="560d7-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="560d7-133">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="560d7-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="560d7-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="560d7-134">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="560d7-135">CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="560d7-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="560d7-136">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="560d7-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
