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
ms.openlocfilehash: 8d8efccde56d8d37a75b1d9bbec706411c6b1f45
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134791"
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="d38d7-102">IGCThreadControl::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d38d7-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="d38d7-103">Bir atık toplama ya da başka bir askıya alma işleminden sonra çalışma zamanının iş parçacıklarını sürdürüyor olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="d38d7-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d38d7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d38d7-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d38d7-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d38d7-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="d38d7-106">'ndaki Çöp toplamanın gerçekleştirildiği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="d38d7-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d38d7-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="d38d7-107">Remarks</span></span>  
 <span data-ttu-id="d38d7-108">`SuspensionEnding` geri çağırma sırasında herhangi bir iş parçacığını yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="d38d7-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d38d7-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d38d7-109">Requirements</span></span>  
 <span data-ttu-id="d38d7-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d38d7-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d38d7-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d38d7-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d38d7-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d38d7-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d38d7-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d38d7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d38d7-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d38d7-114">See also</span></span>

- [<span data-ttu-id="d38d7-115">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d38d7-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
