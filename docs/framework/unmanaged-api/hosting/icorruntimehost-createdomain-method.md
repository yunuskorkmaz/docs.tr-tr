---
title: ICorRuntimeHost::CreateDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9fdacb690b31e7b9930825e5d54ef8fc95bb3a5a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762136"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="72860-102">ICorRuntimeHost::CreateDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="72860-102">ICorRuntimeHost::CreateDomain Method</span></span>
<span data-ttu-id="72860-103">Uygulama etki alanı oluşturur.</span><span class="sxs-lookup"><span data-stu-id="72860-103">Creates an application domain.</span></span> <span data-ttu-id="72860-104">Çağıranın türü bir arabirim işaretçisi alır <xref:System._AppDomain> türde bir örnek <xref:System.AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="72860-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72860-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="72860-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="72860-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="72860-106">Parameters</span></span>  
 `pwzFriendlyName`  
 <span data-ttu-id="72860-107">[in] Etki alanında kolay bir ad vermek için kullanılan isteğe bağlı bir parametre.</span><span class="sxs-lookup"><span data-stu-id="72860-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="72860-108">Bu kolay adı, etki alanını tanımlamak için hata ayıklayıcıları gibi kullanıcı arabirimlerinde görüntülenebilir.</span><span class="sxs-lookup"><span data-stu-id="72860-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="72860-109">[in] İsteğe bağlı bir işaretçiler dizisi `IIdentity` kanıt eşlenmiş bir izin kümesi oluşturmak için Güvenlik İlkesi aracılığıyla temsil eden örnekleri.</span><span class="sxs-lookup"><span data-stu-id="72860-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="72860-110">Bir `IIdentity` nesnesi elde edilebilir çağırarak [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="72860-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="72860-111">[out] Bir arabirim işaretçisi türünde <xref:System._AppDomain> örneğine <xref:System.AppDomain?displayProperty=nameWithType> daha fazla etki alanı kontrol etmek için kullanılabilir.</span><span class="sxs-lookup"><span data-stu-id="72860-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="72860-112">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="72860-112">Return Value</span></span>  
  
|<span data-ttu-id="72860-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="72860-113">HRESULT</span></span>|<span data-ttu-id="72860-114">Açıklama</span><span class="sxs-lookup"><span data-stu-id="72860-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="72860-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="72860-115">S_OK</span></span>|<span data-ttu-id="72860-116">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="72860-116">The operation was successful.</span></span>|  
|<span data-ttu-id="72860-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="72860-117">S_FALSE</span></span>|<span data-ttu-id="72860-118">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="72860-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="72860-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="72860-119">E_FAIL</span></span>|<span data-ttu-id="72860-120">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="72860-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="72860-121">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="72860-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="72860-122">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="72860-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="72860-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="72860-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="72860-124">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="72860-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="72860-125">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="72860-125">Requirements</span></span>  
 <span data-ttu-id="72860-126">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72860-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72860-127">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="72860-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="72860-128">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="72860-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="72860-129">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="72860-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72860-130">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="72860-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="72860-131">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="72860-131">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
