---
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7dfa1dd15f38263ffdfef594ab030867b3fed1de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436783"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="d4454-102">ICorThreadpool::CorCreateTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d4454-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="d4454-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="d4454-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4454-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d4454-104">Syntax</span></span>  
  
```  
HRESULT CorCreateTimer (  
    [in]  HANDLE*             phNewTimer,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Parameter,  
    [in]  DWORD               DueTime,  
    [in]  DWORD               Period,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d4454-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d4454-105">Requirements</span></span>  
 <span data-ttu-id="d4454-106">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4454-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4454-107">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d4454-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d4454-108">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d4454-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d4454-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4454-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4454-110">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d4454-110">See Also</span></span>  
 [<span data-ttu-id="d4454-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d4454-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
