---
title: "ICorThreadpool::CorGetMaxThreads Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorGetMaxThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 066497578f9587da670df5aede4750375c94a7ad
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="f3440-102">ICorThreadpool::CorGetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f3440-102">ICorThreadpool::CorGetMaxThreads Method</span></span>
<span data-ttu-id="f3440-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="f3440-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3440-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f3440-104">Syntax</span></span>  
  
```  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f3440-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f3440-105">Requirements</span></span>  
 <span data-ttu-id="f3440-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3440-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3440-107">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f3440-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f3440-108">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f3440-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f3440-109">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3440-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3440-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f3440-110">See Also</span></span>  
 [<span data-ttu-id="f3440-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f3440-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
