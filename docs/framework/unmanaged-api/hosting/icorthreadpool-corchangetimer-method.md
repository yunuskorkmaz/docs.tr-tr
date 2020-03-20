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
ms.openlocfilehash: bb3778a55e7f395ad65f6a9841ca1f31f1de4ebc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178251"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="457f3-102">ICorThreadpool::CorChangeTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="457f3-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="457f3-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmak üzere tasarlanmamıştır.</span><span class="sxs-lookup"><span data-stu-id="457f3-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="457f3-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="457f3-104">Syntax</span></span>  
  
```cpp  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,
    [in]  ULONG  DueTime,
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="457f3-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="457f3-105">Requirements</span></span>  
 <span data-ttu-id="457f3-106">**Platformlar:** [Bkz. Sistem Gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="457f3-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="457f3-107">**Üstbilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="457f3-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="457f3-108">**Kütüphane:** MSCorEE.dll bir kaynak olarak dahil</span><span class="sxs-lookup"><span data-stu-id="457f3-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="457f3-109">**.NET Çerçeve Sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="457f3-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="457f3-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="457f3-110">See also</span></span>

- [<span data-ttu-id="457f3-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="457f3-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
