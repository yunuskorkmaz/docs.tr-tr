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
ms.openlocfilehash: 20b600eb50ca4992e20b991406d18a91feae5c54
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574462"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="fc2db-102">ICorThreadpool::CorGetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fc2db-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="fc2db-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="fc2db-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2db-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fc2db-104">Syntax</span></span>  
  
```  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fc2db-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fc2db-105">Requirements</span></span>  
 <span data-ttu-id="fc2db-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2db-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2db-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fc2db-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc2db-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fc2db-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc2db-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2db-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2db-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fc2db-110">See also</span></span>
- [<span data-ttu-id="fc2db-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fc2db-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
