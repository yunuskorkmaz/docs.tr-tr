---
description: ': ICorThreadpool:: CorCreateTimer yöntemi hakkında daha fazla bilgi edinin'
title: ICorThreadpool::CorCreateTimer Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorCreateTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorCreateTimer
helpviewer_keywords:
- CorCreateTimer method [.NET Framework hosting]
- ICorThreadpool::CorCreateTimer method [.NET Framework hosting]
ms.assetid: 0d56ef25-30f1-4499-8a1f-76e7654ec614
topic_type:
- apiref
ms.openlocfilehash: dc4258493181430a7e803f3b995e6b32ed2cd8b2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737785"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="6a5ab-103">ICorThreadpool::CorCreateTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6a5ab-103">ICorThreadpool::CorCreateTimer Method</span></span>

<span data-ttu-id="6a5ab-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="6a5ab-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a5ab-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a5ab-105">Syntax</span></span>  
  
```cpp  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="6a5ab-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6a5ab-106">Requirements</span></span>  

 <span data-ttu-id="6a5ab-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a5ab-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6a5ab-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6a5ab-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6a5ab-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6a5ab-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6a5ab-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a5ab-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a5ab-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6a5ab-111">See also</span></span>

- [<span data-ttu-id="6a5ab-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6a5ab-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
