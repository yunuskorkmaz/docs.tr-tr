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
ms.openlocfilehash: 217874e625604613e67170a118a7bc3616e02c4d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139654"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="9fcfa-102">ICorRuntimeHost::CreateDomainSetup Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9fcfa-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>
<span data-ttu-id="9fcfa-103">Bir <xref:System.AppDomainSetup?displayProperty=nameWithType> örneğine IAppDomainSetup türünde bir arabirim işaretçisi alır.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="9fcfa-104">`IAppDomainSetup`, bir uygulama etki alanının oluşturulmadan önce özelliklerini yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fcfa-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9fcfa-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9fcfa-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9fcfa-106">Parameters</span></span>  
 `pAppDomainSetup`  
 <span data-ttu-id="9fcfa-107">dışı <xref:System.AppDomainSetup?displayProperty=nameWithType> örneğine yönelik arabirim işaretçisi.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="9fcfa-108">Bu parametre `IUnknown`olarak yazılır, bu nedenle çağıranlar genellikle `IAppDomainSetup`türünde bir arabirim işaretçisi almak için bu işaretçi üzerinde `QueryInterface` çağırmalıdır.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9fcfa-109">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="9fcfa-109">Return Value</span></span>  
  
|<span data-ttu-id="9fcfa-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="9fcfa-110">HRESULT</span></span>|<span data-ttu-id="9fcfa-111">Açıklama</span><span class="sxs-lookup"><span data-stu-id="9fcfa-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9fcfa-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="9fcfa-112">S_OK</span></span>|<span data-ttu-id="9fcfa-113">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-113">The operation was successful.</span></span>|  
|<span data-ttu-id="9fcfa-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="9fcfa-114">S_FALSE</span></span>|<span data-ttu-id="9fcfa-115">İşlem tamamlanamadı.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="9fcfa-116">E_FAıL</span><span class="sxs-lookup"><span data-stu-id="9fcfa-116">E_FAIL</span></span>|<span data-ttu-id="9fcfa-117">Bilinmeyen, çok zararlı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="9fcfa-118">Bir yöntem E_FAıL döndürürse, ortak dil çalışma zamanı (CLR) işlemde artık kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="9fcfa-119">Herhangi bir barındırma API 'si için sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="9fcfa-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="9fcfa-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="9fcfa-121">CLR bir işleme yüklenmemiş veya CLR yönetilen kodu çalıştıramadığından veya çağrıyı başarıyla işleyemediği bir durumda.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fcfa-122">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9fcfa-122">Remarks</span></span>  
 <span data-ttu-id="9fcfa-123">Bu yöntemden döndürülen işaretçi genellikle [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) metoduna parametre olarak geçirilir.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fcfa-124">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9fcfa-124">Requirements</span></span>  
 <span data-ttu-id="9fcfa-125">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fcfa-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fcfa-126">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9fcfa-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fcfa-127">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9fcfa-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9fcfa-128">**.NET Framework sürümü:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="9fcfa-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fcfa-129">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9fcfa-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="9fcfa-130">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9fcfa-130">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
