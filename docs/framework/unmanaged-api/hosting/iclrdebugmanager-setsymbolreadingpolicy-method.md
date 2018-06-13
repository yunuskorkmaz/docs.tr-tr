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
ms.openlocfilehash: 1ee21861ed3911303d4661721b65e9e147c6953a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33433825"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="69629-102">ICLRDebugManager::SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="69629-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="69629-103">Program veritabanı (PDB) dosyaları okumak için ilke ayarlar.</span><span class="sxs-lookup"><span data-stu-id="69629-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="69629-104">İlke çağrı yığınları satır numaralarını ve dosyalarla ilgili bilgiler dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="69629-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69629-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="69629-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="69629-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="69629-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="69629-107">[in] Üye [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="69629-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="69629-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="69629-108">Return Value</span></span>  
  
|<span data-ttu-id="69629-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="69629-109">HRESULT</span></span>|<span data-ttu-id="69629-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="69629-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="69629-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="69629-111">S_OK</span></span>|<span data-ttu-id="69629-112">`SetSymbolReadingPolicy` başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="69629-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="69629-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="69629-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="69629-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="69629-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="69629-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="69629-115">E_FAIL</span></span>|<span data-ttu-id="69629-116">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="69629-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="69629-117">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="69629-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="69629-118">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="69629-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69629-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="69629-119">Requirements</span></span>  
 <span data-ttu-id="69629-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69629-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69629-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="69629-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="69629-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="69629-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="69629-123">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69629-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69629-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="69629-124">See Also</span></span>  
 [<span data-ttu-id="69629-125">ICLRDebugManager Arabirimi</span><span class="sxs-lookup"><span data-stu-id="69629-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
