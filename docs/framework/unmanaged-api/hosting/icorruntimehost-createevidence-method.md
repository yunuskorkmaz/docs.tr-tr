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
ms.openlocfilehash: 429ce0510162b3256cdf58f4820b04dd80243e29
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139639"
---
# <a name="icorruntimehostcreateevidence-method"></a><span data-ttu-id="c7954-102">ICorRuntimeHost::CreateEvidence Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c7954-102">ICorRuntimeHost::CreateEvidence Method</span></span>
<span data-ttu-id="c7954-103"><xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>türünde bir arabirim işaretçisi alır, bu da konağın [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) veya [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoduna geçirilecek güvenlik kanıtı oluşturmasına olanak tanır.</span><span class="sxs-lookup"><span data-stu-id="c7954-103">Gets an interface pointer of type <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>, which allows the host to create security evidence to pass to the [CreateDomain](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomain-method.md) or [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7954-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c7954-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateEvidence (  
    [out] IUnknown** pEvidence  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7954-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c7954-105">Parameters</span></span>  
 `pEvidence`  
 <span data-ttu-id="c7954-106">dışı Güvenlik kanıtı oluşturmak için kullanılan bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> örneğine yönelik arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="c7954-106">[out] A interface pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType> instance used to create security evidence.</span></span> <span data-ttu-id="c7954-107">Bu işaretçi `IUnknown`yazılır, bu nedenle arayanlar bir <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>işaretçi almak için genellikle bu arabirimdeki `QueryInterface` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="c7954-107">This pointer is typed `IUnknown`, so callers should typically call `QueryInterface` on this interface to obtain a pointer to an <xref:System.Security.Principal.IIdentity?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7954-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c7954-108">Return Value</span></span>  
  
|<span data-ttu-id="c7954-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c7954-109">HRESULT</span></span>|<span data-ttu-id="c7954-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c7954-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c7954-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="c7954-111">S_OK</span></span>|<span data-ttu-id="c7954-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c7954-112">The operation was successful.</span></span>|  
|<span data-ttu-id="c7954-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c7954-113">S_FALSE</span></span>|<span data-ttu-id="c7954-114">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="c7954-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c7954-115">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="c7954-115">E_FAIL</span></span>|<span data-ttu-id="c7954-116">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c7954-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c7954-117">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c7954-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c7954-118">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7954-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c7954-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c7954-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c7954-120">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c7954-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7954-121">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c7954-121">Remarks</span></span>  
 <span data-ttu-id="c7954-122">Bu yöntem, yerel koddan doldurulamadı boş bir koleksiyon döndürür.</span><span class="sxs-lookup"><span data-stu-id="c7954-122">This method returns an empty collection that cannot be populated from native code.</span></span> <span data-ttu-id="c7954-123">Bunun yerine <xref:System.Security.Policy.Evidence> yöntemini kullanmanız gerekir.</span><span class="sxs-lookup"><span data-stu-id="c7954-123">You should use the <xref:System.Security.Policy.Evidence> method instead.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7954-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c7954-124">Requirements</span></span>  
 <span data-ttu-id="c7954-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7954-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7954-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c7954-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c7954-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="c7954-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c7954-128">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="c7954-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7954-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c7954-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="c7954-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c7954-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
