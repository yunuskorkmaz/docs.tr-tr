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
ms.openlocfilehash: b3faffbf9dc85c563dac84fc2e4e4d849db5d42d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59148531"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="2af22-102">ICorThreadpool::CorBindIoCompletionCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2af22-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="2af22-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="2af22-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af22-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2af22-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="2af22-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2af22-105">Requirements</span></span>  
 <span data-ttu-id="2af22-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af22-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af22-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2af22-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2af22-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2af22-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2af22-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af22-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af22-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2af22-110">See also</span></span>

- [<span data-ttu-id="2af22-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2af22-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
