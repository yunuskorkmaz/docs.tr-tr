---
title: IGCHost2::SetGCStartupLimitsEx Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost2::SetGCStartupLimitsEx
helpviewer_keywords:
- IGCHost2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, IGCHost2 interface [.NET Framework hosting]
ms.assetid: bba941c2-1c57-46d3-bbf5-5fb92700c490
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f61f6ed5712f3c98f06f5fa76657f3fa7b70fe84
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666338"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="8f57d-102">IGCHost2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8f57d-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="8f57d-103">Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8f57d-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f57d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8f57d-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="8f57d-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8f57d-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="8f57d-106">[in] Çöp toplama sistem tarafından kullanılan kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="8f57d-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="8f57d-107">[in] Nesil 0 en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="8f57d-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f57d-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8f57d-108">Remarks</span></span>  
 <span data-ttu-id="8f57d-109">Değerleri, `SetGCStartupLimitsEx` kümeleri yalnızca ana bilgisayar başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="8f57d-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="8f57d-110">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8f57d-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8f57d-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8f57d-111">Requirements</span></span>  
 <span data-ttu-id="8f57d-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8f57d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8f57d-113">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="8f57d-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8f57d-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8f57d-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8f57d-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8f57d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f57d-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8f57d-116">See also</span></span>
- [<span data-ttu-id="8f57d-117">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8f57d-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
