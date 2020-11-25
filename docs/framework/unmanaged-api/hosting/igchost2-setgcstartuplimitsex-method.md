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
ms.openlocfilehash: 4dca62903a123765ceb8bb251b79455ad0e4730a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726814"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="fade4-102">IGCHost2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fade4-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="fade4-103">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="fade4-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fade4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="fade4-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fade4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="fade4-105">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="fade4-106">'ndaki Çöp toplama sistemi tarafından kullanılan segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="fade4-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="fade4-107">'ndaki 0 üretimi için en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="fade4-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fade4-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fade4-108">Remarks</span></span>  

 <span data-ttu-id="fade4-109">`SetGCStartupLimitsEx`Ayarlayan değerler yalnızca konak başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="fade4-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="fade4-110">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="fade4-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fade4-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fade4-111">Requirements</span></span>  

 <span data-ttu-id="fade4-112">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fade4-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fade4-113">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="fade4-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="fade4-114">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fade4-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fade4-115">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fade4-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fade4-116">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fade4-116">See also</span></span>

- [<span data-ttu-id="fade4-117">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fade4-117">IGCHost2 Interface</span></span>](igchost2-interface.md)
