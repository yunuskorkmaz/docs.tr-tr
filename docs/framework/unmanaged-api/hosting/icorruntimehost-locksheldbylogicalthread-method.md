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
ms.openlocfilehash: f6ef7e06d94cb22d266949927cb15105b1602d3a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139535"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="92f19-102">ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="92f19-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>
<span data-ttu-id="92f19-103">Geçerli iş parçacığının tuttuğu kilit sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="92f19-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="92f19-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="92f19-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f19-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="92f19-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92f19-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="92f19-106">Parameters</span></span>  
 `pCount`  
 <span data-ttu-id="92f19-107">dışı Geçerli iş parçacığının tuttuğu kilit sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="92f19-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92f19-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="92f19-108">Requirements</span></span>  
 <span data-ttu-id="92f19-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92f19-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92f19-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92f19-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92f19-111">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="92f19-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92f19-112">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="92f19-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92f19-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="92f19-113">See also</span></span>

- [<span data-ttu-id="92f19-114">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="92f19-114">ICorRuntimeHost Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
