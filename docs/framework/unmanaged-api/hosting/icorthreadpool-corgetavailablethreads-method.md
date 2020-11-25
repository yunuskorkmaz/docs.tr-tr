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
ms.openlocfilehash: 09b1f56600c05bf8e6028328adb80083b03ccc13
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725787"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="abd94-102">ICorThreadpool::CorGetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="abd94-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>

<span data-ttu-id="abd94-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="abd94-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abd94-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="abd94-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="abd94-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="abd94-105">Requirements</span></span>  

 <span data-ttu-id="abd94-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abd94-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="abd94-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="abd94-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="abd94-108">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="abd94-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="abd94-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abd94-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abd94-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abd94-110">See also</span></span>

- [<span data-ttu-id="abd94-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="abd94-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
