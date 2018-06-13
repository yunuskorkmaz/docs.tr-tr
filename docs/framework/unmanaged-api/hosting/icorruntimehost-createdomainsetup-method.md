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
ms.openlocfilehash: bf3aff2c3c4d10c4ee805a6110561d6fdcd63a55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437992"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="235a8-102">ICorRuntimeHost::CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="235a8-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="235a8-103">Alır, bir arabirim işaretçisi türü için Iappdomainsetup bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="235a8-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="235a8-104">`IAppDomainSetup` uygulama etki alanı yönlerini oluşturulmadan önce yapılandırmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="235a8-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="235a8-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="235a8-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="235a8-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="235a8-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="235a8-107">[out] Bir arabirim işaretçisi bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="235a8-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="235a8-108">Bu parametre olarak yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` türünde bir arabirim işaretçisi almak için bu işaretçinin üzerinde `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="235a8-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="235a8-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="235a8-109">Return Value</span></span>  
  
|<span data-ttu-id="235a8-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="235a8-110">HRESULT</span></span>|<span data-ttu-id="235a8-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="235a8-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="235a8-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="235a8-112">S_OK</span></span>|<span data-ttu-id="235a8-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="235a8-113">The operation was successful.</span></span>|  
|<span data-ttu-id="235a8-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="235a8-114">S_FALSE</span></span>|<span data-ttu-id="235a8-115">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="235a8-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="235a8-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="235a8-116">E_FAIL</span></span>|<span data-ttu-id="235a8-117">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="235a8-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="235a8-118">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="235a8-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="235a8-119">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="235a8-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="235a8-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="235a8-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="235a8-121">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="235a8-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="235a8-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="235a8-122">Remarks</span></span>  
 <span data-ttu-id="235a8-123">Bu yöntemin döndürdüğü işaretçi genellikle bir parametre olarak geçirilen [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="235a8-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="235a8-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="235a8-124">Requirements</span></span>  
 <span data-ttu-id="235a8-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="235a8-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="235a8-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="235a8-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="235a8-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="235a8-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="235a8-128">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="235a8-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="235a8-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="235a8-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="235a8-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="235a8-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
