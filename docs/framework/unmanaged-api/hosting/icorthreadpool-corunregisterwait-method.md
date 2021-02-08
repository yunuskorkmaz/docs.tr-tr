---
description: ': ICorThreadpool:: CorUnregisterWait Yöntemi hakkında daha fazla bilgi edinin'
title: ICorThreadpool::CorUnregisterWait Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 61b6c7a1fa8459ddd173d2857cff982f353afc31
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789534"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="b444c-103">ICorThreadpool::CorUnregisterWait Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b444c-103">ICorThreadpool::CorUnregisterWait Method</span></span>

<span data-ttu-id="b444c-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="b444c-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b444c-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b444c-105">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="b444c-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b444c-106">Requirements</span></span>  

 <span data-ttu-id="b444c-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b444c-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b444c-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b444c-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b444c-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b444c-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b444c-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b444c-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b444c-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b444c-111">See also</span></span>

- [<span data-ttu-id="b444c-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b444c-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
