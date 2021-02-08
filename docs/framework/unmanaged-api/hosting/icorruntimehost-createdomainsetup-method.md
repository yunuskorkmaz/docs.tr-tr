---
description: ': ICorRuntimeHost:: CreateDomainSetup yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: b7c2dc55fa9f0d3d5a5c18e38c2c825048ae5f53
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789690"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="6bfff-103">ICorRuntimeHost::CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6bfff-103">ICorRuntimeHost::CreateDomainSetup Method</span></span>

<span data-ttu-id="6bfff-104">Bir örneğe IAppDomainSetup türünde bir arabirim işaretçisi alır <xref:System.AppDomainSetup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6bfff-104">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="6bfff-105">`IAppDomainSetup` , bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="6bfff-105">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bfff-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6bfff-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bfff-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6bfff-107">Parameters</span></span>  

 `pAppDomainSetup`  
 <span data-ttu-id="6bfff-108">dışı Bir örneğe yönelik arabirim işaretçisi <xref:System.AppDomainSetup?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="6bfff-108">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="6bfff-109">Bu parametre olarak yazılır `IUnknown` , bu nedenle çağıranlar `QueryInterface` türü bir arabirim işaretçisi almak için genellikle bu işaretçiye çağrı yapmalıdır `IAppDomainSetup` .</span><span class="sxs-lookup"><span data-stu-id="6bfff-109">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6bfff-110">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="6bfff-110">Return Value</span></span>  
  
|<span data-ttu-id="6bfff-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6bfff-111">HRESULT</span></span>|<span data-ttu-id="6bfff-112">Description</span><span class="sxs-lookup"><span data-stu-id="6bfff-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6bfff-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="6bfff-113">S_OK</span></span>|<span data-ttu-id="6bfff-114">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="6bfff-114">The operation was successful.</span></span>|  
|<span data-ttu-id="6bfff-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6bfff-115">S_FALSE</span></span>|<span data-ttu-id="6bfff-116">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="6bfff-116">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6bfff-117">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6bfff-117">E_FAIL</span></span>|<span data-ttu-id="6bfff-118">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="6bfff-118">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6bfff-119">Bir yöntem E_FAIL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="6bfff-119">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6bfff-120">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="6bfff-120">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6bfff-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6bfff-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6bfff-122">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="6bfff-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6bfff-123">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6bfff-123">Remarks</span></span>  

 <span data-ttu-id="6bfff-124">Bu yöntemden döndürülen işaretçi genellikle [CreateDomainEx](icorruntimehost-createdomainex-method.md) metoduna parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="6bfff-124">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bfff-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6bfff-125">Requirements</span></span>  

 <span data-ttu-id="6bfff-126">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bfff-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bfff-127">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6bfff-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bfff-128">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6bfff-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6bfff-129">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="6bfff-129">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bfff-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6bfff-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="6bfff-131">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6bfff-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
