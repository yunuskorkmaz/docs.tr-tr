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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132827"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="110b4-102">ICLRDebugManager::SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="110b4-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="110b4-103">Program veritabanı (PDB) dosyaları okumak için ilkesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="110b4-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="110b4-104">İlke satır numaraları ve dosyaları hakkında bilgi çağrı yığınlarıyla içerilip içerilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="110b4-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="110b4-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="110b4-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="110b4-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="110b4-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="110b4-107">[in] Üye [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) sabit listesi.</span><span class="sxs-lookup"><span data-stu-id="110b4-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="110b4-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="110b4-108">Return Value</span></span>  
  
|<span data-ttu-id="110b4-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="110b4-109">HRESULT</span></span>|<span data-ttu-id="110b4-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="110b4-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="110b4-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="110b4-111">S_OK</span></span>|`SetSymbolReadingPolicy` <span data-ttu-id="110b4-112">başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="110b4-112">returned successfully.</span></span>|  
|<span data-ttu-id="110b4-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="110b4-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="110b4-114">Ortak dil çalışma zamanı (CLR) işlem içine yüklenmemiş olan veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı şekilde işleme bir durumda değil.</span><span class="sxs-lookup"><span data-stu-id="110b4-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="110b4-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="110b4-115">E_FAIL</span></span>|<span data-ttu-id="110b4-116">Bilinmeyen geri dönülemez bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="110b4-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="110b4-117">CLR, artık E_FAIL bir yöntemin dönüşünün ardından, işlem içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="110b4-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="110b4-118">Yöntemleri barındırma yapılan sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="110b4-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="110b4-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="110b4-119">Requirements</span></span>  
 <span data-ttu-id="110b4-120">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="110b4-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="110b4-121">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="110b4-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="110b4-122">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="110b4-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="110b4-123">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="110b4-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="110b4-124">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="110b4-124">See also</span></span>

- [<span data-ttu-id="110b4-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="110b4-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
