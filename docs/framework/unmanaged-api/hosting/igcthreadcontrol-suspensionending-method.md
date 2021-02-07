---
description: 'Daha fazla bilgi edinin: IGCThreadControl:: SuspensionEnding yöntemi'
title: IGCThreadControl::SuspensionEnding Yöntemi
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionEnding
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type:
- apiref
ms.openlocfilehash: 5ff889f45ea3664312060f373907e65c367276f1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709275"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="80595-103">IGCThreadControl::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="80595-103">IGCThreadControl::SuspensionEnding Method</span></span>

<span data-ttu-id="80595-104">Bir atık toplama ya da başka bir askıya alma işleminden sonra çalışma zamanının iş parçacıklarını sürdürüyor olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="80595-104">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80595-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="80595-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="80595-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="80595-106">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="80595-107">'ndaki Çöp toplamanın gerçekleştirildiği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="80595-107">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="80595-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="80595-108">Remarks</span></span>  

 <span data-ttu-id="80595-109">Geri çağırma sırasında herhangi bir iş parçacığını yeniden zamanlamayın `SuspensionEnding` .</span><span class="sxs-lookup"><span data-stu-id="80595-109">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="80595-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="80595-110">Requirements</span></span>  

 <span data-ttu-id="80595-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="80595-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="80595-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="80595-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="80595-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="80595-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="80595-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="80595-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80595-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80595-115">See also</span></span>

- [<span data-ttu-id="80595-116">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="80595-116">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
