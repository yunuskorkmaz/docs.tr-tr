---
title: ICorRuntimeHost::CloseEnum Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f150fe80302cd03e872ca8bdf5d172caae1ce599
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967688"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="33056-102">ICorRuntimeHost::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="33056-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="33056-103">Bir etki alanı Numaralandırıcı tekrar başlangıcını etki alanı listesi sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="33056-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33056-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33056-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33056-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="33056-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="33056-106">[in] Sıfırlamak için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="33056-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="33056-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="33056-107">Return Value</span></span>  
  
|<span data-ttu-id="33056-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="33056-108">HRESULT</span></span>|<span data-ttu-id="33056-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33056-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="33056-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="33056-110">S_OK</span></span>|<span data-ttu-id="33056-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="33056-111">The operation was successful.</span></span>|  
|<span data-ttu-id="33056-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="33056-112">S_FALSE</span></span>|<span data-ttu-id="33056-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="33056-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="33056-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="33056-114">E_FAIL</span></span>|<span data-ttu-id="33056-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="33056-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="33056-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="33056-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="33056-117">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="33056-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="33056-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="33056-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="33056-119">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="33056-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33056-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33056-120">Requirements</span></span>  
 <span data-ttu-id="33056-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33056-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33056-122">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="33056-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="33056-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="33056-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="33056-124">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="33056-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33056-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="33056-125">See also</span></span>

- [<span data-ttu-id="33056-126">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="33056-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="33056-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="33056-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
