---
title: IGCHost::SetGCStartupLimits Yöntemi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e65a83d1da0580436babd15e4f27e2db7a698668
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/30/2019
ms.locfileid: "66377607"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="f8c82-102">IGCHost::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f8c82-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="f8c82-103">Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f8c82-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f8c82-104">.NET Framework 4.5 ile başlayarak, kesim boyutu ve en fazla nesil 0 boyut değerleri büyük ayarlayabilirsiniz `DWORD` kullanarak [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="f8c82-104">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8c82-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f8c82-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8c82-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f8c82-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="f8c82-107">[in] Çöp toplama sistem tarafından kullanılan kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="f8c82-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="f8c82-108">[in] Nesil 0 en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="f8c82-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8c82-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f8c82-109">Remarks</span></span>  
 <span data-ttu-id="f8c82-110">`SetGCStartupLimits` Yöntemi çağrılabilir yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="f8c82-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="f8c82-111">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f8c82-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8c82-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f8c82-112">Requirements</span></span>  
 <span data-ttu-id="f8c82-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8c82-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8c82-114">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="f8c82-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f8c82-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f8c82-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f8c82-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8c82-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8c82-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f8c82-117">See also</span></span>

- [<span data-ttu-id="f8c82-118">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f8c82-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
