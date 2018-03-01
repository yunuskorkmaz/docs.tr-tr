---
title: "ICorRuntimeHost::CloseEnum Yöntemi"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 677ab3a97b7fcceccd8ceb0943c62df8bc999649
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="8111c-102">ICorRuntimeHost::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8111c-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="8111c-103">Bir etki alanı Numaralandırıcı geri etki alanı listesi başlangıç durumuna sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="8111c-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8111c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8111c-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8111c-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8111c-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="8111c-106">[in] Sıfırlama Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="8111c-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8111c-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="8111c-107">Return Value</span></span>  
  
|<span data-ttu-id="8111c-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8111c-108">HRESULT</span></span>|<span data-ttu-id="8111c-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="8111c-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8111c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="8111c-110">S_OK</span></span>|<span data-ttu-id="8111c-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="8111c-111">The operation was successful.</span></span>|  
|<span data-ttu-id="8111c-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="8111c-112">S_FALSE</span></span>|<span data-ttu-id="8111c-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="8111c-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="8111c-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8111c-114">E_FAIL</span></span>|<span data-ttu-id="8111c-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="8111c-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="8111c-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="8111c-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="8111c-117">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="8111c-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8111c-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8111c-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8111c-119">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="8111c-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8111c-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8111c-120">Requirements</span></span>  
 <span data-ttu-id="8111c-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8111c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8111c-122">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8111c-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8111c-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8111c-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8111c-124">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8111c-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8111c-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="8111c-125">See Also</span></span>  
 [<span data-ttu-id="8111c-126">CorBindToRuntimeEx İşlevi</span><span class="sxs-lookup"><span data-stu-id="8111c-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="8111c-127">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8111c-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
