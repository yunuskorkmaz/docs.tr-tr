---
title: ICorRuntimeHost::EnumDomains Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.EnumDomains
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::EnumDomains
helpviewer_keywords:
- ICorRuntimeHost::EnumDomains method [.NET Framework hosting]
- EnumDomains method [.NET Framework hosting]
ms.assetid: 96b74995-0cde-4876-b6df-7fc164e6a5d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 69fcc862e98e305105a6f17ca49940bd10cef39c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937065"
---
# <a name="icorruntimehostenumdomains-method"></a><span data-ttu-id="27f95-102">ICorRuntimeHost::EnumDomains Yöntemi</span><span class="sxs-lookup"><span data-stu-id="27f95-102">ICorRuntimeHost::EnumDomains Method</span></span>
<span data-ttu-id="27f95-103">Bir numaralandırıcı, geçerli işlem için etki alanlarını alır.</span><span class="sxs-lookup"><span data-stu-id="27f95-103">Gets an enumerator for the domains in the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27f95-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="27f95-104">Syntax</span></span>  
  
```  
HRESULT EnumDomains (  
    [out] HCORENUM *hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27f95-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="27f95-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="27f95-106">[out] Etki alanları için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="27f95-106">[out] An enumerator for the domains.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27f95-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="27f95-107">Return Value</span></span>  
  
|<span data-ttu-id="27f95-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="27f95-108">HRESULT</span></span>|<span data-ttu-id="27f95-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="27f95-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="27f95-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="27f95-110">S_OK</span></span>|<span data-ttu-id="27f95-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="27f95-111">The operation was successful.</span></span>|  
|<span data-ttu-id="27f95-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="27f95-112">S_FALSE</span></span>|<span data-ttu-id="27f95-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="27f95-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="27f95-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="27f95-114">E_FAIL</span></span>|<span data-ttu-id="27f95-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="27f95-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="27f95-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="27f95-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="27f95-117">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="27f95-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="27f95-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="27f95-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="27f95-119">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="27f95-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27f95-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="27f95-120">Requirements</span></span>  
 <span data-ttu-id="27f95-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f95-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27f95-122">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="27f95-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27f95-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="27f95-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27f95-124">**.NET framework sürümü:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="27f95-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27f95-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="27f95-125">See also</span></span>

- [<span data-ttu-id="27f95-126">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="27f95-126">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
