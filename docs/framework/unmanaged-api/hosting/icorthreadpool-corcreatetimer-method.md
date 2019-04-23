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
ms.openlocfilehash: 69090618501abe7530ac7a04ae89a6bd3582e029
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111169"
---
# <a name="icorthreadpoolcorcreatetimer-method"></a><span data-ttu-id="7123c-102">ICorThreadpool::CorCreateTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7123c-102">ICorThreadpool::CorCreateTimer Method</span></span>
<span data-ttu-id="7123c-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="7123c-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7123c-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7123c-104">Syntax</span></span>  
  
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
  
## <a name="requirements"></a><span data-ttu-id="7123c-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7123c-105">Requirements</span></span>  
 <span data-ttu-id="7123c-106">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7123c-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7123c-107">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7123c-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7123c-108">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="7123c-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7123c-109">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7123c-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7123c-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7123c-110">See also</span></span>

- [<span data-ttu-id="7123c-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7123c-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
