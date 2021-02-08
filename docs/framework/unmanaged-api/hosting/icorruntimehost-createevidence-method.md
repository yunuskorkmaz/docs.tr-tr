---
description: ': ICorRuntimeHost:: Createkanıt yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 34694f7e867066430a28120b412237ef9c64c740
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789677"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="2fa17-103">ICorRuntimeHost::CreateEvidence Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2fa17-103">ICorRuntimeHost::CreateEvidence Method</span></span>

<span data-ttu-id="2fa17-104"><xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, Konağın [CreateDomain](icorruntimehost-createdomain-method.md) veya [CreateDomainEx](icorruntimehost-createdomainex-method.md) metoduna geçirilecek güvenlik kanıtı oluşturmasına izin veren, türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="2fa17-104">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](icorruntimehost-createdomain-method.md) or [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fa17-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2fa17-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fa17-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="2fa17-106">Parameters</span></span>  

 `pEvidence`  
 <span data-ttu-id="2fa17-107">dışı <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> Güvenlik kanıtı oluşturmak için kullanılan bir örneğe yönelik arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="2fa17-107">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="2fa17-108">Bu işaretçi yazılır `IUnknown` , bu nedenle çağıranlar `QueryInterface` bir işaretçi almak için tipik olarak bu arabirimi çağırmalıdır <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="2fa17-108">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2fa17-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="2fa17-109">Return Value</span></span>  
  
|<span data-ttu-id="2fa17-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2fa17-110">HRESULT</span></span>|<span data-ttu-id="2fa17-111">Description</span><span class="sxs-lookup"><span data-stu-id="2fa17-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2fa17-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="2fa17-112">S_OK</span></span>|<span data-ttu-id="2fa17-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="2fa17-113">The operation was successful.</span></span>|  
|<span data-ttu-id="2fa17-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="2fa17-114">S_FALSE</span></span>|<span data-ttu-id="2fa17-115">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="2fa17-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="2fa17-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2fa17-116">E_FAIL</span></span>|<span data-ttu-id="2fa17-117">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="2fa17-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="2fa17-118">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="2fa17-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="2fa17-119">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fa17-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="2fa17-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2fa17-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2fa17-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="2fa17-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2fa17-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2fa17-122">Remarks</span></span>  

 <span data-ttu-id="2fa17-123">Bu yöntem, yerel koddan doldurulamadı boş bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="2fa17-123">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="2fa17-124"><xref:System.Security.Policy.Evidence>Bunun yerine yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="2fa17-124">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fa17-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2fa17-125">Requirements</span></span>  

 <span data-ttu-id="2fa17-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2fa17-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fa17-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2fa17-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2fa17-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2fa17-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fa17-129">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="2fa17-129">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fa17-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2fa17-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="2fa17-131">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2fa17-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
