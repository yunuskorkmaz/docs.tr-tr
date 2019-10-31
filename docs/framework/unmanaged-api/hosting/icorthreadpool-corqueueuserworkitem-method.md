---
title: ICorThreadpool::CorQueueUserWorkItem Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorQueueUserWorkItem
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorQueueUserWorkItem
helpviewer_keywords:
- ICorThreadpool::CorQueueUserWorkItem method [.NET Framework hosting]
- CorQueueUserWorkItem method [.NET Framework hosting]
ms.assetid: 29ac7898-a7c7-433e-8f79-cd5237e0bab8
topic_type:
- apiref
ms.openlocfilehash: e4a62cc35de18f91324bfd428c24bb329fc9783b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133255"
---
# <a name="icorthreadpoolcorqueueuserworkitem-method"></a><span data-ttu-id="68874-102">ICorThreadpool::CorQueueUserWorkItem Yöntemi</span><span class="sxs-lookup"><span data-stu-id="68874-102">ICorThreadpool::CorQueueUserWorkItem Method</span></span>
<span data-ttu-id="68874-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="68874-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68874-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="68874-104">Syntax</span></span>  
  
```cpp  
HRESULT CorQueueUserWorkItem (  
    [in] LPTHREAD_START_ROUTINE Function,  
    [in] PVOID                  Context,  
    [in] BOOL                   executeOnlyOnce,  
    [out] BOOL*                 result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="68874-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="68874-105">Requirements</span></span>  
 <span data-ttu-id="68874-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68874-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68874-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="68874-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="68874-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="68874-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="68874-109">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68874-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68874-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="68874-110">See also</span></span>

- [<span data-ttu-id="68874-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="68874-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
