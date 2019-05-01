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
ms.openlocfilehash: 365261883f0b81884bb7cf70614628c05f9067c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61993271"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="68884-102">IGCHost::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68884-102">IGCHost::SetGCStartupLimits Method</span></span>
<span data-ttu-id="68884-103">Nesil 0 için kesim boyutu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="68884-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68884-104">İle başlayarak [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], kesim boyutu ayarlayabileceğiniz ve en fazla nesil 0 boyutu daha büyük değerler `DWORD` kullanarak [Igchost2::setgcstartuplimitsex](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="68884-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68884-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68884-105">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68884-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="68884-106">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="68884-107">[in] Çöp toplama sistem tarafından kullanılan kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="68884-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="68884-108">[in] Nesil 0 en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="68884-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68884-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="68884-109">Remarks</span></span>  
 <span data-ttu-id="68884-110">`SetGCStartupLimits` Yöntemi çağrılabilir yalnızca bir kez.</span><span class="sxs-lookup"><span data-stu-id="68884-110">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="68884-111">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="68884-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68884-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68884-112">Requirements</span></span>  
 <span data-ttu-id="68884-113">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68884-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68884-114">**Üst bilgi:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="68884-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="68884-115">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="68884-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68884-116">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68884-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68884-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68884-117">See also</span></span>

- [<span data-ttu-id="68884-118">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68884-118">IGCHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)
