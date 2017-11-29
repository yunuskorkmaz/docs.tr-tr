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
ms.openlocfilehash: c63e4345815a073fe6aa422018b6fadf45bd5370
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="3df64-102">ICorRuntimeHost::EnumDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3df64-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="3df64-103">Bir Numaralandırıcı geçerli işlem için etki alanları alır.</span><span class="sxs-lookup"><span data-stu-id="3df64-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df64-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3df64-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3df64-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3df64-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="3df64-106">[out] Etki alanları için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="3df64-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3df64-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="3df64-107">Return Value</span></span>  
  
|<span data-ttu-id="3df64-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="3df64-108">HRESULT</span></span>|<span data-ttu-id="3df64-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="3df64-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3df64-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="3df64-110">S_OK</span></span>|<span data-ttu-id="3df64-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="3df64-111">The operation was successful.</span></span>|  
|<span data-ttu-id="3df64-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="3df64-112">S_FALSE</span></span>|<span data-ttu-id="3df64-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="3df64-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="3df64-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="3df64-114">E_FAIL</span></span>|<span data-ttu-id="3df64-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="3df64-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="3df64-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="3df64-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="3df64-117">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="3df64-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="3df64-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="3df64-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="3df64-119">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="3df64-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3df64-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3df64-120">Requirements</span></span>  
 <span data-ttu-id="3df64-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3df64-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3df64-122">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3df64-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3df64-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3df64-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3df64-124">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="3df64-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3df64-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="3df64-125">See Also</span></span>  
 [<span data-ttu-id="3df64-126">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="3df64-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
