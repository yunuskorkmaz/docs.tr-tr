---
description: 'Daha fazla bilgi edinin: IGCHost2:: SetGCStartupLimitsEx yöntemi'
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
ms.openlocfilehash: 32d3bcbb467a1a418c7123779c881c46e983edef
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709314"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="dab54-103">IGCHost2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dab54-103">IGCHost2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="dab54-104">Oluşturma 0 ' nın segment boyutunu ve en büyük boyutunu ayarlar.</span><span class="sxs-lookup"><span data-stu-id="dab54-104">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab54-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dab54-105">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dab54-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dab54-106">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="dab54-107">'ndaki Çöp toplama sistemi tarafından kullanılan segmentin boyutu.</span><span class="sxs-lookup"><span data-stu-id="dab54-107">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="dab54-108">'ndaki 0 üretimi için en büyük boyut.</span><span class="sxs-lookup"><span data-stu-id="dab54-108">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dab54-109">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dab54-109">Remarks</span></span>  

 <span data-ttu-id="dab54-110">`SetGCStartupLimitsEx`Ayarlayan değerler yalnızca konak başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="dab54-110">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="dab54-111">Bu değerler daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="dab54-111">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dab54-112">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dab54-112">Requirements</span></span>  

 <span data-ttu-id="dab54-113">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dab54-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dab54-114">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="dab54-114">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="dab54-115">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="dab54-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dab54-116">**.NET Framework sürümleri:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dab54-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dab54-117">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dab54-117">See also</span></span>

- [<span data-ttu-id="dab54-118">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dab54-118">IGCHost2 Interface</span></span>](igchost2-interface.md)
