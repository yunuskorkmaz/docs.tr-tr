---
title: "ICLRDebugManager::SetSymbolReadingPolicy Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDebugManager.SetSymbolReadingPolicy
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d116883c39b4400451ede07df83ac77893ce285c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="0f3eb-102">ICLRDebugManager::SetSymbolReadingPolicy Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0f3eb-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>
<span data-ttu-id="0f3eb-103">Program veritabanı (PDB) dosyaları okumak için ilke ayarlar.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="0f3eb-104">İlke çağrı yığınları satır numaralarını ve dosyalarla ilgili bilgiler dahil edilip edilmeyeceğini belirler.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f3eb-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0f3eb-105">Syntax</span></span>  
  
```  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0f3eb-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0f3eb-106">Parameters</span></span>  
 `policy`  
 <span data-ttu-id="0f3eb-107">[in] Üye [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) numaralandırması.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-107">[in] A member of the [ESymbolReadingPolicy](../../../../docs/framework/unmanaged-api/hosting/esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f3eb-108">Dönüş Değeri</span><span class="sxs-lookup"><span data-stu-id="0f3eb-108">Return Value</span></span>  
  
|<span data-ttu-id="0f3eb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0f3eb-109">HRESULT</span></span>|<span data-ttu-id="0f3eb-110">Açıklama</span><span class="sxs-lookup"><span data-stu-id="0f3eb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0f3eb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0f3eb-111">S_OK</span></span>|<span data-ttu-id="0f3eb-112">`SetSymbolReadingPolicy`başarıyla döndürüldü.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="0f3eb-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0f3eb-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0f3eb-114">Ortak dil çalışma zamanı (CLR) süreç içine yüklü değil veya CLR içinde yönetilen kod çalıştıramaz veya çağrı başarılı bir şekilde işlemek bir durumda.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0f3eb-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0f3eb-115">E_FAIL</span></span>|<span data-ttu-id="0f3eb-116">Bilinmeyen yıkıcı bir hata oluştu.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0f3eb-117">CLR, artık bir yöntem E_FAIL döndükten sonra işlemi içinde kullanılamaz.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0f3eb-118">Yöntemleri barındırma sonraki çağrılar HOST_E_CLRNOTAVAILABLE döndürür.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0f3eb-119">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0f3eb-119">Requirements</span></span>  
 <span data-ttu-id="0f3eb-120">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0f3eb-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f3eb-121">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0f3eb-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0f3eb-122">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0f3eb-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0f3eb-123">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f3eb-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f3eb-124">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0f3eb-124">See Also</span></span>  
 [<span data-ttu-id="0f3eb-125">Iclrdebugmanager arabirimi</span><span class="sxs-lookup"><span data-stu-id="0f3eb-125">ICLRDebugManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)
