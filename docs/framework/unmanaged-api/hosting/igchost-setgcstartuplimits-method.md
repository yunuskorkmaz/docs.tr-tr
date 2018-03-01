---
title: "IGCHost::SetGCStartupLimits Yöntemi"
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
- IGCHost.SetGCStartupLimits
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCStartupLimits
helpviewer_keywords:
- SetGCStartupLimits method, IGCHost interface [.NET Framework hosting]
- IGCHost::SetGCStartupLimits method [.NET Framework hosting]
ms.assetid: cae53926-82ac-4d1d-b297-0bde0bd1bebb
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d99212b1ece4d3c0ce9440ac973b8254ebca6dde
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="71441-102">IGCHost::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71441-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="71441-103">Kesim boyutu ve en büyük boyutu 0 oluşturma için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="71441-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="71441-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kesim boyutu ayarlayabilir ve en fazla kuşak 0 boyutuna büyük değerler `DWORD` kullanarak [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="71441-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71441-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="71441-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="71441-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="71441-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="71441-107">[in] Çöp toplama sistem tarafından kullanılan kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="71441-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="71441-108">[in] Oluşturma 0 için en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="71441-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71441-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="71441-109">Remarks</span></span>  
 <span data-ttu-id="71441-110">`SetGCStartupLimits` Yöntemi çağrılabilir yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="71441-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="71441-111">Bu değerleri daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="71441-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71441-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71441-112">Requirements</span></span>  
 <span data-ttu-id="71441-113">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71441-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71441-114">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="71441-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="71441-115">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="71441-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71441-116">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71441-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71441-117">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="71441-117">See Also</span></span>  
 [<span data-ttu-id="71441-118">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71441-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
