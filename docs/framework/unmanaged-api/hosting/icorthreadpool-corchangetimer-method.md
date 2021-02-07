---
description: ': ICorThreadpool:: CorChangeTimer yöntemi hakkında daha fazla bilgi edinin'
title: ICorThreadpool::CorChangeTimer Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorChangeTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorChangeTimer
helpviewer_keywords:
- CorChangeTimer method [.NET Framework hosting]
- ICorThreadpool::CorChangeTimer method [.NET Framework hosting]
ms.assetid: 82b03a59-5a87-43ed-9b75-e04b256e1a46
topic_type:
- apiref
ms.openlocfilehash: 259974d7c04f0bf0b4cc6b93234b35ab2c96e2ae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99672003"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="d6ef8-103">ICorThreadpool::CorChangeTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d6ef8-103">ICorThreadpool::CorChangeTimer Method</span></span>

<span data-ttu-id="d6ef8-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="d6ef8-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6ef8-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d6ef8-105">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d6ef8-106">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d6ef8-106">Requirements</span></span>  

 <span data-ttu-id="d6ef8-107">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d6ef8-107">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6ef8-108">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d6ef8-108">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d6ef8-109">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d6ef8-109">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6ef8-110">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6ef8-110">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6ef8-111">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d6ef8-111">See also</span></span>

- [<span data-ttu-id="d6ef8-112">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d6ef8-112">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
