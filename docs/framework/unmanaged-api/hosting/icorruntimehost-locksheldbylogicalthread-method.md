---
title: ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.LocksHeldByLogicalThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread
helpviewer_keywords:
- ICorRuntimeHost::LocksHeldByLogicalThread method [.NET Framework hosting]
- LocksHeldByLogicalThread method [.NET Framework hosting]
ms.assetid: c3601255-d894-4d7c-b1df-c31334551700
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 90af015de4428f75330de89978a7fc0a4b26750b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59144202"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="8c5bc-102">ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="8c5bc-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="8c5bc-103">Geçerli iş parçacığı tutan kilitleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="8c5bc-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="8c5bc-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="8c5bc-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c5bc-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="8c5bc-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c5bc-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="8c5bc-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="8c5bc-107">[out] Geçerli iş parçacığı tutan kilit sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="8c5bc-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8c5bc-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="8c5bc-108">Requirements</span></span>  
 <span data-ttu-id="8c5bc-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c5bc-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c5bc-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="8c5bc-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c5bc-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="8c5bc-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c5bc-112">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="8c5bc-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c5bc-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="8c5bc-113">See also</span></span>

- [<span data-ttu-id="8c5bc-114">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="8c5bc-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
