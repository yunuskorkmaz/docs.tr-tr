---
title: ICorThreadpool::CorSetMaxThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
ms.openlocfilehash: e0183ed0f1556afb660ead042dd0d26a63ef75dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133221"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="9ad10-102">ICorThreadpool::CorSetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9ad10-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="9ad10-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="9ad10-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ad10-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9ad10-104">Syntax</span></span>  
  
```cpp  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9ad10-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9ad10-105">Requirements</span></span>  
 <span data-ttu-id="9ad10-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ad10-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ad10-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="9ad10-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9ad10-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="9ad10-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9ad10-109">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ad10-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ad10-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9ad10-110">See also</span></span>

- [<span data-ttu-id="9ad10-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9ad10-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
