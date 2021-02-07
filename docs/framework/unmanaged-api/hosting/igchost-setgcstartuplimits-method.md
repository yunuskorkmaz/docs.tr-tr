---
description: 'Daha fazla bilgi edinin: IGCHost:: SetGCStartupLimits yöntemi'
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
ms.openlocfilehash: 91c74d54189bbfb7e9f208e507fe6e75b7023e00
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709509"
---
# <a name="igchostsetgcstartuplimits-method"></a><span data-ttu-id="8ec23-103">IGCHost::SetGCStartupLimits Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8ec23-103">IGCHost::SetGCStartupLimits Method</span></span>

<span data-ttu-id="8ec23-104">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="8ec23-104">Sets the segment size and the maximum size for generation 0.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8ec23-105">4,5 .NET Framework başlayarak, segment boyutunu ve en fazla nesil 0 boyutunu `DWORD` [IGCHost2:: SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) yöntemini kullanarak daha büyük değerlere ayarlayabilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="8ec23-105">Starting with the .NET Framework 4.5, you can set segment size and maximum generation 0 size to values greater than `DWORD` by using the [IGCHost2::SetGCStartupLimitsEx](igchost2-setgcstartuplimitsex-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8ec23-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8ec23-106">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimits (  
    [in] DWORD SegmentSize,  
    [in] DWORD MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8ec23-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8ec23-107">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="8ec23-108">'ndaki Çöp toplama sistemi tarafından kullanılan segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="8ec23-108">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="8ec23-109">'ndaki 0 üretimi için en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="8ec23-109">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8ec23-110">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="8ec23-110">Remarks</span></span>  

 <span data-ttu-id="8ec23-111">`SetGCStartupLimits`Yöntemi yalnızca bir kez çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="8ec23-111">The `SetGCStartupLimits` method may be called only once.</span></span> <span data-ttu-id="8ec23-112">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="8ec23-112">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8ec23-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8ec23-113">Requirements</span></span>  

 <span data-ttu-id="8ec23-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8ec23-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8ec23-115">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="8ec23-115">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="8ec23-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="8ec23-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8ec23-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8ec23-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ec23-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8ec23-118">See also</span></span>

- [<span data-ttu-id="8ec23-119">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8ec23-119">IGCHost Interface</span></span>](igchost-interface.md)
