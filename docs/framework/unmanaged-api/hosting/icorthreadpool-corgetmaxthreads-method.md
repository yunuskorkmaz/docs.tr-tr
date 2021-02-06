---
description: ': ICorThreadpool:: CorGetMaxThreads yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 44de36a7ff3e086ab9389049137c66697af11af3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636488"
---
# <a name="icorthreadpoolcorgetmaxthreads-method"></a><span data-ttu-id="fd177-103">ICorThreadpool::CorGetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fd177-103">ICorThreadpool::CorGetMaxThreads Method</span></span>

<span data-ttu-id="fd177-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="fd177-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd177-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="fd177-105">Syntax</span></span>  
  
```cpp  
HRESULT CorGetMaxThreads (  
    [out] DWORD *MaxWorkerThreads,  
    [out] DWORD *MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="fd177-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fd177-106">Requirements</span></span>  

 <span data-ttu-id="fd177-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd177-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd177-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fd177-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fd177-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fd177-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fd177-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd177-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd177-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fd177-111">See also</span></span>

- [<span data-ttu-id="fd177-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fd177-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
