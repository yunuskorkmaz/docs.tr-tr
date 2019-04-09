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
ms.openlocfilehash: da5e90055a08227ea7cb7fa1b459fe6f5f3a81fc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59127341"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="80323-102">IGCHost2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80323-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="80323-103">Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="80323-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80323-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80323-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80323-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80323-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="80323-106">[in] Çöp toplama sistem tarafından kullanılan kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="80323-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="80323-107">[in] Nesil 0 en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="80323-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80323-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80323-108">Remarks</span></span>  
 <span data-ttu-id="80323-109">Değerleri, `SetGCStartupLimitsEx` kümeleri yalnızca ana bilgisayar başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="80323-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="80323-110">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="80323-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80323-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80323-111">Requirements</span></span>  
 <span data-ttu-id="80323-112">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80323-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80323-113">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="80323-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="80323-114">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="80323-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="80323-115">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="80323-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="80323-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80323-116">See also</span></span>

- [<span data-ttu-id="80323-117">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80323-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
