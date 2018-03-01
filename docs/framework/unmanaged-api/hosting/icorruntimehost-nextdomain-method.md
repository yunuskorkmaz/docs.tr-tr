---
title: "ICorRuntimeHost::NextDomain Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0e539cd4071fe9713ed53f66c2f67b24b787d259
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostnextdomain-method"></a><span data-ttu-id="ded8a-102">ICorRuntimeHost::NextDomain Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ded8a-102">ICorRuntimeHost::NextDomain Method</span></span>
<span data-ttu-id="ded8a-103">Arabirim işaretçisi sonraki etki alanına numaralandırmada alır.</span><span class="sxs-lookup"><span data-stu-id="ded8a-103">Gets an interface pointer to the next domain in the enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ded8a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ded8a-104">Syntax</span></span>  
  
```  
HRESULT NextDomain (  
    [in] HCORENUM hEnum,  
    [out] void** pAppDomain  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ded8a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ded8a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="ded8a-106">[in] Bir çağrı aracılığıyla edinilen Numaralandırıcı [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span><span class="sxs-lookup"><span data-stu-id="ded8a-106">[in] The enumerator that was obtained through a call to [EnumDomains](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-enumdomains-method.md).</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="ded8a-107">[out] Bir arabirim işaretçisi <xref:System._AppDomain?displayProperty=nameWithType> hiçbir daha fazla etki alanı varsa numaralandırma veya null, sonraki etki alanı temsil eden tür.</span><span class="sxs-lookup"><span data-stu-id="ded8a-107">[out] An interface pointer to the <xref:System._AppDomain?displayProperty=nameWithType> type that represents the next domain in the enumeration, or null, if no more domains exist.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ded8a-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="ded8a-108">Return Value</span></span>  
  
|<span data-ttu-id="ded8a-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="ded8a-109">HRESULT</span></span>|<span data-ttu-id="ded8a-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="ded8a-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="ded8a-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="ded8a-111">S_OK</span></span>|<span data-ttu-id="ded8a-112">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="ded8a-112">The operation was successful.</span></span>|  
|<span data-ttu-id="ded8a-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="ded8a-113">S_FALSE</span></span>|<span data-ttu-id="ded8a-114">İşlemi tamamlamak başarısız oldu veya sabit listede daha fazla hiçbir etki alanı yoktur.</span><span class="sxs-lookup"><span data-stu-id="ded8a-114">The operation failed to complete, or there are no more domains in the enumeration.</span></span>|  
|<span data-ttu-id="ded8a-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="ded8a-115">E_FAIL</span></span>|<span data-ttu-id="ded8a-116">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="ded8a-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="ded8a-117">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="ded8a-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="ded8a-118">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="ded8a-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="ded8a-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="ded8a-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="ded8a-120">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="ded8a-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ded8a-121">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ded8a-121">Requirements</span></span>  
 <span data-ttu-id="ded8a-122">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ded8a-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ded8a-123">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ded8a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ded8a-124">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ded8a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ded8a-125">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="ded8a-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ded8a-126">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ded8a-126">See Also</span></span>  
 <xref:System._AppDomain>  
 <xref:System.AppDomain>  
 [<span data-ttu-id="ded8a-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ded8a-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
