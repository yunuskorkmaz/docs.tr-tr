---
title: ICorRuntimeHost::CreateDomainSetup Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 88f5de9882f8a029769d0ccbdac21aec541582a4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59157371"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="6df7b-102">ICorRuntimeHost::CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6df7b-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="6df7b-103">Alır, bir arabirim işaretçisi türü için Iappdomainsetup bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="6df7b-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="6df7b-104">`IAppDomainSetup` oluşturulmadan önce bir uygulama etki alanı yönlerini yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6df7b-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6df7b-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6df7b-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6df7b-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6df7b-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="6df7b-107">[out] Bir arabirim işaretçisi için bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="6df7b-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="6df7b-108">Bu parametre olarak yazılan `IUnknown`, Arayanların genellikle çağırmalıdır `QueryInterface` Bu işaretçinin türü bir arabirim işaretçisini almak için `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="6df7b-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6df7b-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6df7b-109">Return Value</span></span>  
  
|<span data-ttu-id="6df7b-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6df7b-110">HRESULT</span></span>|<span data-ttu-id="6df7b-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="6df7b-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6df7b-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6df7b-112">S_OK</span></span>|<span data-ttu-id="6df7b-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="6df7b-113">The operation was successful.</span></span>|  
|<span data-ttu-id="6df7b-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6df7b-114">S_FALSE</span></span>|<span data-ttu-id="6df7b-115">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="6df7b-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6df7b-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6df7b-116">E_FAIL</span></span>|<span data-ttu-id="6df7b-117">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6df7b-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6df7b-118">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6df7b-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6df7b-119">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6df7b-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6df7b-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6df7b-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6df7b-121">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6df7b-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6df7b-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6df7b-122">Remarks</span></span>  
 <span data-ttu-id="6df7b-123">Bu yöntemi tarafından döndürülen işaretçi genellikle bir parametre olarak geçirilen [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="6df7b-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6df7b-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6df7b-124">Requirements</span></span>  
 <span data-ttu-id="6df7b-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6df7b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6df7b-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6df7b-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6df7b-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6df7b-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6df7b-128">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="6df7b-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6df7b-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6df7b-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="6df7b-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6df7b-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
