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
ms.openlocfilehash: a3a2d1827774ddedc00eb849f64256e3f425b3fa
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127719"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="cdbd9-102">ICorRuntimeHost::CreateDomainEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbd9-102">ICorRuntimeHost::CreateDomainEx Method</span></span>
<span data-ttu-id="cdbd9-103">Bir uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-103">Creates an application domain.</span></span> <span data-ttu-id="cdbd9-104">Çağıran, <xref:System.AppDomain?displayProperty=nameWithType>türünde bir örneğe <xref:System._AppDomain>türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="cdbd9-105">Bu yöntem, çağıranın döndürülen <xref:System._AppDomain> örneğinin ek özelliklerini yapılandırmak için bir IAppDomainSetup örneği geçişine olanak sağlar.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdbd9-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cdbd9-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdbd9-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="cdbd9-107">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="cdbd9-108">'ndaki Etki alanına kolay bir ad vermek için kullanılan isteğe bağlı bir parametre.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="cdbd9-109">Bu kolay ad, etki alanını tanımlamak için hata ayıklayıcılar gibi kullanıcı arabirimlerinde gösterilebilir.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="cdbd9-110">'ndaki [ICorRuntimeHost:: CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) yöntemine yapılan bir çağrı ile elde edilen `IAppDomainSetup`türünde isteğe bağlı bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="cdbd9-111">'ndaki Bir izin kümesi oluşturmak için güvenlik ilkesiyle eşlenen kanıtları temsil eden `IIdentity` örneklerine yönelik bir işaretçi dizisi.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="cdbd9-112">`IIdentity` nesnesi [Createkanıt](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi çağırarak elde edilebilir.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="cdbd9-113">dışı Etki alanını daha fazla denetlemek için kullanılabilecek bir <xref:System.AppDomain?displayProperty=nameWithType> örneğine <xref:System._AppDomain> türünde bir arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cdbd9-114">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="cdbd9-114">Return Value</span></span>  
  
|<span data-ttu-id="cdbd9-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cdbd9-115">HRESULT</span></span>|<span data-ttu-id="cdbd9-116">Açıklama</span><span class="sxs-lookup"><span data-stu-id="cdbd9-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cdbd9-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="cdbd9-117">S_OK</span></span>|<span data-ttu-id="cdbd9-118">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-118">The operation was successful.</span></span>|  
|<span data-ttu-id="cdbd9-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="cdbd9-119">S_FALSE</span></span>|<span data-ttu-id="cdbd9-120">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="cdbd9-121">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="cdbd9-121">E_FAIL</span></span>|<span data-ttu-id="cdbd9-122">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="cdbd9-123">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="cdbd9-124">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="cdbd9-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cdbd9-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cdbd9-126">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cdbd9-127">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cdbd9-127">Remarks</span></span>  
 <span data-ttu-id="cdbd9-128">`CreateDomainEx`, çağıranın uygulama etki alanını yapılandırmak için özellik değerleriyle `IAppDomainSetup` bir örnek geçmesine izin vererek [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) 'ın yeteneklerini genişletir.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-128">`CreateDomainEx` extends the capabilities of [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdbd9-129">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cdbd9-129">Requirements</span></span>  
 <span data-ttu-id="cdbd9-130">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdbd9-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdbd9-131">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cdbd9-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cdbd9-132">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cdbd9-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cdbd9-133">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="cdbd9-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdbd9-134">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cdbd9-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="cdbd9-135">CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cdbd9-135">CreateDomain Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="cdbd9-136">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cdbd9-136">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
