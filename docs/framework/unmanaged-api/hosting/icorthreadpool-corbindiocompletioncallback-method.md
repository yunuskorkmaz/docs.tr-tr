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
ms.openlocfilehash: c3ebe0bcd546feeeb0aa8c962f2b4c8b0562cb6f
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760452"
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="8aec0-102">ICorThreadpool::CorBindIoCompletionCallback Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8aec0-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="8aec0-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="8aec0-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aec0-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="8aec0-104">Syntax</span></span>  
  
```cpp  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="8aec0-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8aec0-105">Requirements</span></span>  
 <span data-ttu-id="8aec0-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aec0-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aec0-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8aec0-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8aec0-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="8aec0-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8aec0-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aec0-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aec0-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8aec0-110">See also</span></span>

- [<span data-ttu-id="8aec0-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8aec0-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
