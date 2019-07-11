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
ms.openlocfilehash: bfddd1d8f6fed105224cb2294d68f3f0bc016403
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67762157"
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="8a2f0-102">ICorRuntimeHost::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8a2f0-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="8a2f0-103">Bir etki alanı Numaralandırıcı tekrar başlangıcını etki alanı listesi sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a2f0-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8a2f0-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a2f0-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8a2f0-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8a2f0-106">[in] Sıfırlamak için bir numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8a2f0-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8a2f0-107">Return Value</span></span>  
  
|<span data-ttu-id="8a2f0-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8a2f0-108">HRESULT</span></span>|<span data-ttu-id="8a2f0-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8a2f0-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8a2f0-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8a2f0-110">S_OK</span></span>|<span data-ttu-id="8a2f0-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-111">The operation was successful.</span></span>|  
|<span data-ttu-id="8a2f0-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8a2f0-112">S_FALSE</span></span>|<span data-ttu-id="8a2f0-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8a2f0-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8a2f0-114">E_FAIL</span></span>|<span data-ttu-id="8a2f0-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8a2f0-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8a2f0-117">Herhangi bir barındırma API'si yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8a2f0-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8a2f0-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8a2f0-119">CLR'yi bir işleme yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8a2f0-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8a2f0-120">Requirements</span></span>  
 <span data-ttu-id="8a2f0-121">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a2f0-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a2f0-122">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8a2f0-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8a2f0-123">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8a2f0-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8a2f0-124">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8a2f0-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a2f0-125">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8a2f0-125">See also</span></span>

- [<span data-ttu-id="8a2f0-126">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="8a2f0-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [<span data-ttu-id="8a2f0-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8a2f0-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
