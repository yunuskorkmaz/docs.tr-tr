---
title: "ICorRuntimeHost::CreateDomainSetup Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateDomainSetup
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ca09788ea403e2a60d6de0cb6834fdc90261b770
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="ab301-102">ICorRuntimeHost::CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ab301-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="ab301-103">Alır, bir arabirim işaretçisi türü için Iappdomainsetup bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="ab301-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="ab301-104">`IAppDomainSetup`uygulama etki alanı yönlerini oluşturulmadan önce yapılandırmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="ab301-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab301-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ab301-105">Syntax</span></span>  
  
```  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab301-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ab301-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="ab301-107">[out] Bir arabirim işaretçisi bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneği.</span><span class="sxs-lookup"><span data-stu-id="ab301-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="ab301-108">Bu parametre olarak yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` türünde bir arabirim işaretçisi almak için bu işaretçinin üzerinde `IAppDomainSetup`.</span><span class="sxs-lookup"><span data-stu-id="ab301-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ab301-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ab301-109">Return Value</span></span>  
  
|<span data-ttu-id="ab301-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ab301-110">HRESULT</span></span>|<span data-ttu-id="ab301-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ab301-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ab301-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="ab301-112">S_OK</span></span>|<span data-ttu-id="ab301-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ab301-113">The operation was successful.</span></span>|  
|<span data-ttu-id="ab301-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ab301-114">S_FALSE</span></span>|<span data-ttu-id="ab301-115">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="ab301-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="ab301-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ab301-116">E_FAIL</span></span>|<span data-ttu-id="ab301-117">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ab301-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ab301-118">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ab301-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ab301-119">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ab301-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ab301-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ab301-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ab301-121">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ab301-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab301-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ab301-122">Remarks</span></span>  
 <span data-ttu-id="ab301-123">Bu yöntemin döndürdüğü işaretçi genellikle bir parametre olarak geçirilen [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="ab301-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab301-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ab301-124">Requirements</span></span>  
 <span data-ttu-id="ab301-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab301-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab301-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ab301-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab301-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ab301-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab301-128">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ab301-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab301-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ab301-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 <xref:System.AppDomainSetup>  
 <xref:System.IAppDomainSetup?displayProperty=nameWithType>  
 [<span data-ttu-id="ab301-130">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="ab301-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
