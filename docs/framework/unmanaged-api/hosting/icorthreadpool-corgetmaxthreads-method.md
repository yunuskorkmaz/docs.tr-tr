---
title: ICorThreadpool::CorGetMaxThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorGetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGetMaxThreads
helpviewer_keywords:
- CorGetMaxThreads method [.NET Framework hosting]
- ICorThreadpool::CorGetMaxThreads method [.NET Framework hosting]
ms.assetid: 2861533a-cda0-47b3-b716-0d363505289b
topic_type:
- apiref
ms.openlocfilehash: 511b6e463bcd0d975cf7be96f870baefe27fc77b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720522"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="5e130-102">ICorThreadpool::CorGetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5e130-102">ICorThreadpool::CorGetMaxThreads Method</span></span>

<span data-ttu-id="5e130-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="5e130-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e130-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e130-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5e130-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5e130-105">Requirements</span></span>  

 <span data-ttu-id="5e130-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e130-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e130-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5e130-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e130-108">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="5e130-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e130-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e130-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e130-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5e130-110">See also</span></span>

- [<span data-ttu-id="5e130-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5e130-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
