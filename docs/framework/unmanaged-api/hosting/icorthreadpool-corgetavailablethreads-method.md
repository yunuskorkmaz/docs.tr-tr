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
ms.openlocfilehash: e5c11cfe21303aca6b867951ad610cddc58a0f03
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83762766"
---
# <a name="icorthreadpoolcorgetavailablethreads-method"></a><span data-ttu-id="b3d99-102">ICorThreadpool::CorGetAvailableThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3d99-102">ICorThreadpool::CorGetAvailableThreads Method</span></span>
<span data-ttu-id="b3d99-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="b3d99-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d99-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="b3d99-104">Syntax</span></span>  
  
```cpp  
HRESULT CorGetAvailableThreads (  
    [out] DWORD *AvailableWorkerThreads,  
    [out] DWORD *AvailableIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b3d99-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3d99-105">Requirements</span></span>  
 <span data-ttu-id="b3d99-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3d99-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3d99-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3d99-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3d99-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="b3d99-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3d99-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3d99-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3d99-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3d99-110">See also</span></span>

- [<span data-ttu-id="b3d99-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3d99-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
