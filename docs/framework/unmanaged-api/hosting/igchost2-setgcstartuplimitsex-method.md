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
ms.openlocfilehash: f92667191cad163998d233e1110365de65c0340c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437696"
---
# <a name="igchost2setgcstartuplimitsex-method"></a><span data-ttu-id="f480f-102">IGCHost2::SetGCStartupLimitsEx Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f480f-102">IGCHost2::SetGCStartupLimitsEx Method</span></span>
<span data-ttu-id="f480f-103">Kesim boyutu ve en büyük boyutu 0 oluşturma için ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f480f-103">Sets the segment size and the maximum size for generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f480f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f480f-104">Syntax</span></span>  
  
```  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,  
    [in] SIZE_T MaxGen0Size  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f480f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="f480f-105">Parameters</span></span>  
 `SegmentSize`  
 <span data-ttu-id="f480f-106">[in] Çöp toplama sistem tarafından kullanılan kesim boyutu.</span><span class="sxs-lookup"><span data-stu-id="f480f-106">[in] The size of the segment used by the garbage collection system.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="f480f-107">[in] Oluşturma 0 için en büyük boyutu.</span><span class="sxs-lookup"><span data-stu-id="f480f-107">[in] The maximum size for generation 0.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f480f-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f480f-108">Remarks</span></span>  
 <span data-ttu-id="f480f-109">Değerleri, `SetGCStartupLimitsEx` kümeleri yalnızca ana başlatılmadan önce belirtilebilir.</span><span class="sxs-lookup"><span data-stu-id="f480f-109">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="f480f-110">Bu değerleri daha sonra değiştirilemez.</span><span class="sxs-lookup"><span data-stu-id="f480f-110">These values cannot be changed later.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f480f-111">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f480f-111">Requirements</span></span>  
 <span data-ttu-id="f480f-112">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f480f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f480f-113">**Başlık:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="f480f-113">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="f480f-114">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f480f-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f480f-115">**.NET framework sürümleri:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f480f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f480f-116">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f480f-116">See Also</span></span>  
 [<span data-ttu-id="f480f-117">IGCHost2 Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f480f-117">IGCHost2 Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)
