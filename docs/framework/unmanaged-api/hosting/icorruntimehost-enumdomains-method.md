---
title: "ICorRuntimeHost::EnumDomains Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.EnumDomains
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f12135134e38b3f52c66aa951d61a3da7cf5fa50
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="fbb7a-102">ICorRuntimeHost::EnumDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fbb7a-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="fbb7a-103">Bir Numaralandırıcı geçerli işlem için etki alanları alır.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbb7a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fbb7a-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fbb7a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fbb7a-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="fbb7a-106">[out] Etki alanları için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbb7a-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="fbb7a-107">Return Value</span></span>  
  
|<span data-ttu-id="fbb7a-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fbb7a-108">HRESULT</span></span>|<span data-ttu-id="fbb7a-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="fbb7a-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fbb7a-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="fbb7a-110">S_OK</span></span>|<span data-ttu-id="fbb7a-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-111">The operation was successful.</span></span>|  
|<span data-ttu-id="fbb7a-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="fbb7a-112">S_FALSE</span></span>|<span data-ttu-id="fbb7a-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="fbb7a-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fbb7a-114">E_FAIL</span></span>|<span data-ttu-id="fbb7a-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="fbb7a-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="fbb7a-117">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="fbb7a-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fbb7a-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fbb7a-119">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fbb7a-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fbb7a-120">Requirements</span></span>  
 <span data-ttu-id="fbb7a-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fbb7a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fbb7a-122">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fbb7a-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fbb7a-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fbb7a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fbb7a-124">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="fbb7a-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbb7a-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="fbb7a-125">See Also</span></span>  
 [<span data-ttu-id="fbb7a-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fbb7a-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
