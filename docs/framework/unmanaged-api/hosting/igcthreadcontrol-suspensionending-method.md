---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ffee1550c64f1ce7c438580ce78a497aeeb99f3a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468773"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="dcf79-102">IGCThreadControl::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="dcf79-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="dcf79-103">Konak, çalışma zamanı iş parçacıklarının çöp toplama ya da diğer ertelenmesi sonra sürdürülmekte bildirir.</span><span class="sxs-lookup"><span data-stu-id="dcf79-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf79-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="dcf79-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dcf79-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="dcf79-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="dcf79-106">[in] Bir atık toplama işlemi gerçekleştirildikten oluşturma.</span><span class="sxs-lookup"><span data-stu-id="dcf79-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dcf79-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="dcf79-107">Remarks</span></span>  
 <span data-ttu-id="dcf79-108">Herhangi bir iş parçacığı sırasında yeniden değil `SuspensionEnding` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="dcf79-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf79-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="dcf79-109">Requirements</span></span>  
 <span data-ttu-id="dcf79-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf79-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf79-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dcf79-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dcf79-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="dcf79-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dcf79-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf79-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf79-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="dcf79-114">See also</span></span>
- [<span data-ttu-id="dcf79-115">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="dcf79-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
