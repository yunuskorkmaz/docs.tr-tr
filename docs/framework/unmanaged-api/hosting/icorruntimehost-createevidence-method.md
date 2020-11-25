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
ms.openlocfilehash: 6627fce519934177aefd26a612e5b00ca1941d02
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715673"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="5e578-102">ICorRuntimeHost::CreateEvidence Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e578-102">ICorRuntimeHost::CreateEvidence Method</span></span>

<span data-ttu-id="5e578-103"><xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, Konağın [CreateDomain](icorruntimehost-createdomain-method.md) veya [CreateDomainEx](icorruntimehost-createdomainex-method.md) metoduna geçirilecek güvenlik kanıtı oluşturmasına izin veren, türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="5e578-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e578-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5e578-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5e578-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="5e578-105">Parameters</span></span>  

 `pEvidence`  
 <span data-ttu-id="5e578-106">dışı <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> Güvenlik kanıtı oluşturmak için kullanılan bir örneğe yönelik arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="5e578-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="5e578-107">Bu işaretçi yazılır `IUnknown` , bu nedenle çağıranlar `QueryInterface` bir işaretçi almak için tipik olarak bu arabirimi çağırmalıdır <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e578-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5e578-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="5e578-108">Return Value</span></span>  
  
|<span data-ttu-id="5e578-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="5e578-109">HRESULT</span></span>|<span data-ttu-id="5e578-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="5e578-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="5e578-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="5e578-111">S_OK</span></span>|<span data-ttu-id="5e578-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="5e578-112">The operation was successful.</span></span>|  
|<span data-ttu-id="5e578-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="5e578-113">S_FALSE</span></span>|<span data-ttu-id="5e578-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="5e578-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="5e578-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="5e578-115">E_FAIL</span></span>|<span data-ttu-id="5e578-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="5e578-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="5e578-117">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="5e578-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="5e578-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e578-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="5e578-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="5e578-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="5e578-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="5e578-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e578-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5e578-121">Remarks</span></span>  

 <span data-ttu-id="5e578-122">Bu yöntem, yerel koddan doldurulamadı boş bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="5e578-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="5e578-123"><xref:System.Security.Policy.Evidence>Bunun yerine yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="5e578-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e578-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e578-124">Requirements</span></span>  

 <span data-ttu-id="5e578-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e578-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e578-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5e578-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e578-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5e578-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e578-128">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="5e578-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e578-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e578-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="5e578-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e578-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
