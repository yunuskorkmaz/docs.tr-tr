---
title: ICLRDebugManager::SetSymbolReadingPolicy Yöntemi
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2dc3d350f5c97736b3b65c814a668195aceef2b0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132827"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="e63ed-102">ICLRDebugManager::SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e63ed-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="e63ed-103">Program veritabanı (PDB) dosyaları okumak için ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="e63ed-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="e63ed-104">İlke satır numaraları ve dosyaları hakkında bilgi çağrı yığınlarıyla içerilip içerilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="e63ed-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e63ed-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e63ed-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e63ed-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e63ed-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="e63ed-107">[in] Üye [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="e63ed-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e63ed-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="e63ed-108">Return Value</span></span>  
  
|<span data-ttu-id="e63ed-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="e63ed-109">HRESULT</span></span>|<span data-ttu-id="e63ed-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e63ed-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e63ed-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="e63ed-111">S_OK</span></span>|<span data-ttu-id="e63ed-112">`SetSymbolReadingPolicy` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="e63ed-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="e63ed-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="e63ed-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="e63ed-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="e63ed-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="e63ed-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="e63ed-115">E_FAIL</span></span>|<span data-ttu-id="e63ed-116">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="e63ed-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="e63ed-117">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="e63ed-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="e63ed-118">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="e63ed-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e63ed-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e63ed-119">Requirements</span></span>  
 <span data-ttu-id="e63ed-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e63ed-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e63ed-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e63ed-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e63ed-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e63ed-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e63ed-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e63ed-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e63ed-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e63ed-124">See also</span></span>

- [<span data-ttu-id="e63ed-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e63ed-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
