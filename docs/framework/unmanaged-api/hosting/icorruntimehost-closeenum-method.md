---
title: "ICorRuntimeHost::CloseEnum Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.CloseEnum
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::CloseEnum
helpviewer_keywords:
- CloseEnum method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::CloseEnum method [.NET Framework hosting]
ms.assetid: f7ce7e8c-0a3e-4587-a180-063e2b85940e
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b44797f6efaf8904e3df876e9278a977c912ac6e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="icorruntimehostcloseenum-method"></a><span data-ttu-id="99310-102">ICorRuntimeHost::CloseEnum Yöntemi</span><span class="sxs-lookup"><span data-stu-id="99310-102">ICorRuntimeHost::CloseEnum Method</span></span>
<span data-ttu-id="99310-103">Bir etki alanı Numaralandırıcı geri etki alanı listesi başlangıç durumuna sıfırlar.</span><span class="sxs-lookup"><span data-stu-id="99310-103">Resets a domain enumerator back to the beginning of the domain list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99310-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="99310-104">Syntax</span></span>  
  
```  
HRESULT CloseEnum (  
    [in] HCORENUM hEnum  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="99310-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="99310-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="99310-106">[in] Sıfırlama Numaralandırıcı.</span><span class="sxs-lookup"><span data-stu-id="99310-106">[in] The enumerator to reset.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99310-107">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="99310-107">Return Value</span></span>  
  
|<span data-ttu-id="99310-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="99310-108">HRESULT</span></span>|<span data-ttu-id="99310-109">Açıklama</span><span class="sxs-lookup"><span data-stu-id="99310-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="99310-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="99310-110">S_OK</span></span>|<span data-ttu-id="99310-111">İşlem başarılı oldu.</span><span class="sxs-lookup"><span data-stu-id="99310-111">The operation was successful.</span></span>|  
|<span data-ttu-id="99310-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="99310-112">S_FALSE</span></span>|<span data-ttu-id="99310-113">İşlemi tamamlayamadı.</span><span class="sxs-lookup"><span data-stu-id="99310-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="99310-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="99310-114">E_FAIL</span></span>|<span data-ttu-id="99310-115">Bilinmeyen, geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="99310-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="99310-116">Ortak dil çalışma zamanı (CLR), artık bir yöntem E_FAIL döndürürse, işlemde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="99310-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="99310-117">Barındırma hiçbir API'leri yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="99310-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="99310-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="99310-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="99310-119">CLR süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="99310-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="99310-120">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="99310-120">Requirements</span></span>  
 <span data-ttu-id="99310-121">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99310-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99310-122">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="99310-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="99310-123">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="99310-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="99310-124">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="99310-124">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99310-125">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="99310-125">See Also</span></span>  
 [<span data-ttu-id="99310-126">CorBindToRuntimeEx işlevi</span><span class="sxs-lookup"><span data-stu-id="99310-126">CorBindToRuntimeEx Function</span></span>](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)  
 [<span data-ttu-id="99310-127">Icorruntimehost arabirimi</span><span class="sxs-lookup"><span data-stu-id="99310-127">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
