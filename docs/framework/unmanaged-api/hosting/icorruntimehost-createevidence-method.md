---
title: ICorRuntimeHost::CreateEvidence Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateEvidence
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateEvidence
helpviewer_keywords:
- CreateEvidence method [.NET Framework hosting]
- ICorRuntimeHost::CreateEvidence method [.NET Framework hosting]
ms.assetid: e235ea80-b84c-4442-a4c3-fc96c25a8eb9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ca54f779d257314b843838d90ca9996f1eb3237b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936909"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="da0a3-102">ICorRuntimeHost::CreateEvidence Yöntemi</span><span class="sxs-lookup"><span data-stu-id="da0a3-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="da0a3-103">Türü bir arabirim işaretçisi alır <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, geçirilecek güvenlik kanıt oluşturmak için ana sağlayan [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) veya [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="da0a3-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da0a3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="da0a3-104">Syntax</span></span>  
  
```  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da0a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="da0a3-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="da0a3-106">[out] Bir arabirim işaretçisi için bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> güvenlik kanıt oluşturmak için kullanılan bir örnek.</span><span class="sxs-lookup"><span data-stu-id="da0a3-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="da0a3-107">Bu işaretçinin türü belirtilmiş `IUnknown`, Arayanların genellikle çağırmalıdır `QueryInterface` bir işaretçi alma için bu arabirimdeki bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="da0a3-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="da0a3-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="da0a3-108">Return Value</span></span>  
  
|<span data-ttu-id="da0a3-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="da0a3-109">HRESULT</span></span>|<span data-ttu-id="da0a3-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="da0a3-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="da0a3-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="da0a3-111">S_OK</span></span>|<span data-ttu-id="da0a3-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="da0a3-112">The operation was successful.</span></span>|  
|<span data-ttu-id="da0a3-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="da0a3-113">S_FALSE</span></span>|<span data-ttu-id="da0a3-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="da0a3-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="da0a3-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="da0a3-115">E_FAIL</span></span>|<span data-ttu-id="da0a3-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="da0a3-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="da0a3-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="da0a3-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="da0a3-118">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="da0a3-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="da0a3-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="da0a3-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="da0a3-120">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="da0a3-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="da0a3-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="da0a3-121">Remarks</span></span>  
 <span data-ttu-id="da0a3-122">Bu yöntem, yerel koddan doldurulamaz boş bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="da0a3-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="da0a3-123">Kullanmanız gereken <xref:System.Security.Policy.Evidence> yöntemi yerine.</span><span class="sxs-lookup"><span data-stu-id="da0a3-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da0a3-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="da0a3-124">Requirements</span></span>  
 <span data-ttu-id="da0a3-125">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da0a3-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da0a3-126">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="da0a3-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="da0a3-127">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="da0a3-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="da0a3-128">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="da0a3-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da0a3-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="da0a3-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="da0a3-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="da0a3-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
