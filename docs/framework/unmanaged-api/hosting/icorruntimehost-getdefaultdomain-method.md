---
title: ICorRuntimeHost::GetDefaultDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fe80050d7b513bce2660b81c5e4faa35b375f22b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780032"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="99f7b-102">ICorRuntimeHost::GetDefaultDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99f7b-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>
<span data-ttu-id="99f7b-103">Türü bir arabirim işaretçisi alır <xref:System._AppDomain?displayProperty=nameWithType> , geçerli işlem için varsayılan etki alanı temsil eder.</span><span class="sxs-lookup"><span data-stu-id="99f7b-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99f7b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99f7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99f7b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99f7b-105">Parameters</span></span>  
 `pAppDomain`  
 <span data-ttu-id="99f7b-106">[out] Bir arabirim işaretçisi türünde <xref:System._AppDomain?displayProperty=nameWithType> için <xref:System.AppDomain> işlem için varsayılan uygulama etki alanı temsil eden örneği.</span><span class="sxs-lookup"><span data-stu-id="99f7b-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="99f7b-107">Bu işaretçinin türü belirtilmiş `IUnknown`, Arayanların genellikle çağırmalıdır `QueryInterface` bir arabirim işaretçisi türü elde etmek için <xref:System._AppDomain?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="99f7b-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99f7b-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99f7b-108">Return Value</span></span>  
  
|<span data-ttu-id="99f7b-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99f7b-109">HRESULT</span></span>|<span data-ttu-id="99f7b-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99f7b-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99f7b-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="99f7b-111">S_OK</span></span>|<span data-ttu-id="99f7b-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="99f7b-112">The operation was successful.</span></span>|  
|<span data-ttu-id="99f7b-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="99f7b-113">S_FALSE</span></span>|<span data-ttu-id="99f7b-114">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="99f7b-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="99f7b-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99f7b-115">E_FAIL</span></span>|<span data-ttu-id="99f7b-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="99f7b-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="99f7b-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99f7b-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="99f7b-118">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="99f7b-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="99f7b-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99f7b-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99f7b-120">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="99f7b-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99f7b-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99f7b-121">Requirements</span></span>  
 <span data-ttu-id="99f7b-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99f7b-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99f7b-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99f7b-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99f7b-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="99f7b-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99f7b-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="99f7b-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f7b-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="99f7b-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="99f7b-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="99f7b-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
