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
ms.openlocfilehash: d46881b76685fd04f8bc5e3a67830e58f85cd774
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436682"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="1e850-102">ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1e850-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="1e850-103">Geçerli iş parçacığının tutan kilitleri sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="1e850-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="1e850-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="1e850-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e850-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1e850-105">Syntax</span></span>  
  
```  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1e850-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1e850-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="1e850-107">[out] Geçerli iş parçacığının tutan kilit sayısı için bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="1e850-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e850-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1e850-108">Requirements</span></span>  
 <span data-ttu-id="1e850-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e850-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e850-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1e850-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1e850-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1e850-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1e850-112">**.NET framework sürümleri:** 1.0, 1.1</span><span class="sxs-lookup"><span data-stu-id="1e850-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e850-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1e850-113">See Also</span></span>  
 [<span data-ttu-id="1e850-114">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1e850-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
