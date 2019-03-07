---
title: ICorRuntimeHost::NextDomain Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.NextDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::NextDomain
helpviewer_keywords:
- ICorRuntimeHost::NextDomain method [.NET Framework hosting]
- NextDomain method [.NET Framework hosting]
ms.assetid: fe07a05b-f6d6-44b5-ab01-b9a6eb15c350
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101e1c83d040f2f6db4585e76e4b353270dd1de1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484985"
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="4f711-102">ICorRuntimeHost::NextDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4f711-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="4f711-103">Bir arabirim işaretçisi için bir sonraki etki alanına numaralandırmada alır.</span><span class="sxs-lookup"><span data-stu-id="4f711-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f711-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4f711-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f711-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4f711-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="4f711-106">[in] Bir çağrı aracılığıyla edinilen Numaralandırıcı [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="4f711-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="4f711-107">[out] Bir arabirim işaretçisine <xref:System._AppDomain?displayProperty=nameWithType> hiçbir daha fazla etki alanı varsa bir sonraki etki alanına numaralandırma veya null temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="4f711-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4f711-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="4f711-108">Return Value</span></span>  
  
|<span data-ttu-id="4f711-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4f711-109">HRESULT</span></span>|<span data-ttu-id="4f711-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4f711-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f711-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="4f711-111">S_OK</span></span>|<span data-ttu-id="4f711-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="4f711-112">The operation was successful.</span></span>|  
|<span data-ttu-id="4f711-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="4f711-113">S_FALSE</span></span>|<span data-ttu-id="4f711-114">İşlemi tamamlamak başarısız oldu veya numaralandırmada hiçbir daha fazla etki alanı yoktur.</span><span class="sxs-lookup"><span data-stu-id="4f711-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="4f711-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4f711-115">E_FAIL</span></span>|<span data-ttu-id="4f711-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="4f711-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="4f711-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="4f711-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="4f711-118">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="4f711-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4f711-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4f711-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4f711-120">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="4f711-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4f711-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4f711-121">Requirements</span></span>  
 <span data-ttu-id="4f711-122">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f711-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f711-123">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4f711-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4f711-124">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4f711-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4f711-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="4f711-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f711-126">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4f711-126">See also</span></span>
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="4f711-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4f711-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
