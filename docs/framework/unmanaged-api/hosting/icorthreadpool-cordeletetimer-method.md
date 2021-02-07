---
description: ': ICorThreadpool:: CorDeleteTimer yöntemi hakkında daha fazla bilgi edinin'
title: ICorThreadpool::CorDeleteTimer Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
ms.openlocfilehash: 9096f9969702d522427640b2f881cae4aa23284d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737750"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="3070e-103">ICorThreadpool::CorDeleteTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3070e-103">ICorThreadpool::CorDeleteTimer Method</span></span>

<span data-ttu-id="3070e-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="3070e-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3070e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3070e-105">Syntax</span></span>  
  
```cpp  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="3070e-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3070e-106">Requirements</span></span>  

 <span data-ttu-id="3070e-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3070e-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3070e-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3070e-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3070e-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3070e-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3070e-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3070e-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3070e-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3070e-111">See also</span></span>

- [<span data-ttu-id="3070e-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3070e-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
