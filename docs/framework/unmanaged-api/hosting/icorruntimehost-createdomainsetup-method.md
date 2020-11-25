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
ms.openlocfilehash: 1be7eee5c2591f26c33572446080a4fa4b3b929d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723902"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="c1b8f-102">ICorRuntimeHost::CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c1b8f-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>

<span data-ttu-id="c1b8f-103">Bir örneğe IAppDomainSetup türünde bir arabirim işaretçisi alır <xref:System.AppDomainSetup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c1b8f-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="c1b8f-104">`IAppDomainSetup` , bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b8f-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="c1b8f-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1b8f-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="c1b8f-106">Parameters</span></span>  

 `pAppDomainSetup`  
 <span data-ttu-id="c1b8f-107">dışı Bir örneğe yönelik arabirim işaretçisi <xref:System.AppDomainSetup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="c1b8f-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="c1b8f-108">Bu parametre olarak yazılır `IUnknown` , bu nedenle çağıranlar `QueryInterface` türü bir arabirim işaretçisi almak için genellikle bu işaretçiye çağrı yapmalıdır `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="c1b8f-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c1b8f-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="c1b8f-109">Return Value</span></span>  
  
|<span data-ttu-id="c1b8f-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="c1b8f-110">HRESULT</span></span>|<span data-ttu-id="c1b8f-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="c1b8f-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="c1b8f-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="c1b8f-112">S_OK</span></span>|<span data-ttu-id="c1b8f-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-113">The operation was successful.</span></span>|  
|<span data-ttu-id="c1b8f-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="c1b8f-114">S_FALSE</span></span>|<span data-ttu-id="c1b8f-115">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="c1b8f-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="c1b8f-116">E_FAIL</span></span>|<span data-ttu-id="c1b8f-117">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="c1b8f-118">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="c1b8f-119">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="c1b8f-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="c1b8f-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="c1b8f-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1b8f-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c1b8f-122">Remarks</span></span>  

 <span data-ttu-id="c1b8f-123">Bu yöntemden döndürülen işaretçi genellikle [CreateDomainEx](icorruntimehost-createdomainex-method.md) metoduna parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1b8f-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c1b8f-124">Requirements</span></span>  

 <span data-ttu-id="c1b8f-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1b8f-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1b8f-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c1b8f-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c1b8f-127">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c1b8f-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c1b8f-128">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="c1b8f-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1b8f-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c1b8f-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="c1b8f-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c1b8f-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
