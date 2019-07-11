---
title: ICorThreadpool::CorGetAvailableThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetAvailableThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetAvailableThreads
helpviewer_keywords:
- CorGetAvailableThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetAvailableThreads method [.NET Framework hosting]
ms.assetid: 0b09b750-0b86-4ba4-9621-041857cfe8ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 43d22e5b6fcbbb006d9745942ca94434ee64c08c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751320"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="9939c-102">ICorThreadpool::CorGetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9939c-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="9939c-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="9939c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9939c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9939c-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="9939c-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9939c-105">Requirements</span></span>  
 <span data-ttu-id="9939c-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9939c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9939c-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9939c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9939c-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9939c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9939c-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9939c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9939c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9939c-110">See also</span></span>

- [<span data-ttu-id="9939c-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9939c-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
