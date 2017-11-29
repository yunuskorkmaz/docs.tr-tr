---
title: "ICorRuntimeHost::CreateEvidence Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CreateEvidence
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9c050d8d610b32d2e8421a5d61e36cee151085e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="b4d98-102">ICorRuntimeHost::CreateEvidence Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b4d98-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="b4d98-103">Arabirim işaretçisi türü alır <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, geçirilecek güvenlik bulgu oluşturmak için ana sağlayan [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) veya [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="b4d98-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d98-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b4d98-104">Syntax</span></span>  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4d98-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b4d98-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="b4d98-106">[out] Arabirim işaretçisi bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> güvenlik bulgu oluşturmak için kullanılan örnek.</span><span class="sxs-lookup"><span data-stu-id="b4d98-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="b4d98-107">Bu işaretçinin yazılan `IUnknown`, arayanlar genellikle çağırmalıdır `QueryInterface` gösteren bir işaretçi almak için bu arabirimdeki bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b4d98-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4d98-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="b4d98-108">Return Value</span></span>  
  
|<span data-ttu-id="b4d98-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="b4d98-109">HRESULT</span></span>|<span data-ttu-id="b4d98-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="b4d98-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="b4d98-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4d98-111">S_OK</span></span>|<span data-ttu-id="b4d98-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="b4d98-112">The operation was successful.</span></span>|  
|<span data-ttu-id="b4d98-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b4d98-113">S_FALSE</span></span>|<span data-ttu-id="b4d98-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="b4d98-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="b4d98-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="b4d98-115">E_FAIL</span></span>|<span data-ttu-id="b4d98-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="b4d98-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="b4d98-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="b4d98-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="b4d98-118">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4d98-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="b4d98-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="b4d98-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="b4d98-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="b4d98-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d98-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b4d98-121">Remarks</span></span>  
 <span data-ttu-id="b4d98-122">Bu yöntem, yerel koddan doldurulamaz boş bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="b4d98-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="b4d98-123">Kullanmanız gereken <xref:System.Security.Policy.Evidence> yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="b4d98-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d98-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b4d98-124">Requirements</span></span>  
 <span data-ttu-id="b4d98-125">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d98-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d98-126">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b4d98-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b4d98-127">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b4d98-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b4d98-128">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="b4d98-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d98-129">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b4d98-129">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="b4d98-130">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="b4d98-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
