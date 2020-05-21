---
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
ms.openlocfilehash: e2174afe0ee96bd153b7b40c73c0185d9058a0dc
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760357"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="5ab54-102">ICorThreadpool::CorChangeTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ab54-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="5ab54-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="5ab54-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ab54-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5ab54-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5ab54-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ab54-105">Requirements</span></span>  
 <span data-ttu-id="5ab54-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ab54-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ab54-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ab54-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ab54-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5ab54-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ab54-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ab54-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ab54-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ab54-110">See also</span></span>

- [<span data-ttu-id="5ab54-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ab54-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
