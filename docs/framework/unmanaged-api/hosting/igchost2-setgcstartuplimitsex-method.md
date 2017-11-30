---
title: "IGCHost2::SetGCStartupLimitsEx Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCHost2.SetGCStartupLimitsEx
api_location: mscoree.dll
api_type: COM
f1_keywords: IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ae924447e38dfec8d365fe6cdc85e5dccb028714
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="24664-102">IGCHost2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="24664-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="24664-103">Kesim boyutu ve en büyük boyutu 0 oluşturma için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="24664-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24664-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="24664-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="24664-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="24664-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="24664-106">[in] Çöp toplama sistem tarafından kullanılan kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="24664-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="24664-107">[in] Oluşturma 0 için en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="24664-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24664-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="24664-108">Remarks</span></span>  
 <span data-ttu-id="24664-109">Değerleri, `SetGCStartupLimitsEx` kümeleri yalnızca ana başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="24664-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="24664-110">Bu değerleri daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="24664-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24664-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="24664-111">Requirements</span></span>  
 <span data-ttu-id="24664-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24664-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24664-113">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="24664-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="24664-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="24664-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24664-115">**.NET framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24664-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24664-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="24664-116">See Also</span></span>  
 [<span data-ttu-id="24664-117">Igchost2 arabirimi</span><span class="sxs-lookup"><span data-stu-id="24664-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
