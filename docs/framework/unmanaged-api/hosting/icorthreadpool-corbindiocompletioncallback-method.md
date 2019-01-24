---
title: ICorThreadpool::CorBindIoCompletionCallback Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorBindIoCompletionCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5efd9811b0d5bfd16b802f0d504d69a4e7522833
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707862"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="7f78b-102">ICorThreadpool::CorBindIoCompletionCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7f78b-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="7f78b-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="7f78b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f78b-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7f78b-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7f78b-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7f78b-105">Requirements</span></span>  
 <span data-ttu-id="7f78b-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f78b-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f78b-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7f78b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7f78b-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7f78b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f78b-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f78b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f78b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7f78b-110">See also</span></span>
- [<span data-ttu-id="7f78b-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7f78b-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
