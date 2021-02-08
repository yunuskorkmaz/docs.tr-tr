---
description: ': ICorThreadpool:: CorBindIoCompletionCallback yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 9f9e62fd8947c3ab80c4434814ee7e95b5327a24
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799440"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="d4d82-103">ICorThreadpool::CorBindIoCompletionCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4d82-103">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>

<span data-ttu-id="d4d82-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="d4d82-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4d82-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4d82-105">Syntax</span></span>  
  
```cpp  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d4d82-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4d82-106">Requirements</span></span>  

 <span data-ttu-id="d4d82-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4d82-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4d82-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d4d82-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4d82-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d4d82-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4d82-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4d82-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4d82-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d4d82-111">See also</span></span>

- [<span data-ttu-id="d4d82-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4d82-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
