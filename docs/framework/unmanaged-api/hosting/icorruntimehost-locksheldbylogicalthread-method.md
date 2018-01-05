---
title: "ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.LocksHeldByLogicalThread
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7875d78415d06a55c11a6b42476ff806a5cadc78
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="de19c-102">ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="de19c-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="de19c-103">Geçerli iş parçacığının tutan kilitleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="de19c-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="de19c-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="de19c-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de19c-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="de19c-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de19c-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="de19c-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="de19c-107">[out] Geçerli iş parçacığının tutan kilit sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="de19c-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de19c-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="de19c-108">Requirements</span></span>  
 <span data-ttu-id="de19c-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de19c-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de19c-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="de19c-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="de19c-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="de19c-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de19c-112">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="de19c-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de19c-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="de19c-113">See Also</span></span>  
 [<span data-ttu-id="de19c-114">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="de19c-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
