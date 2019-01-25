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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 288c00ff95bbbe970ab14659b5c720edfcb84320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498706"
---
# <a name="icorthreadpoolcorchangetimer-method"></a><span data-ttu-id="f1715-102">ICorThreadpool::CorChangeTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f1715-102">ICorThreadpool::CorChangeTimer Method</span></span>
<span data-ttu-id="f1715-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="f1715-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1715-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="f1715-104">Syntax</span></span>  
  
```  
HRESULT CorChangeTimer (  
    [in]  HANDLE Timer,   
    [in]  ULONG  DueTime,   
    [in]  ULONG  Period,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="f1715-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f1715-105">Requirements</span></span>  
 <span data-ttu-id="f1715-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1715-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1715-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f1715-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f1715-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f1715-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f1715-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1715-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1715-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f1715-110">See also</span></span>
- [<span data-ttu-id="f1715-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f1715-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
