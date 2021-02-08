---
description: ': ICorRuntimeHost:: LocksHeldByLogicalThread yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: bd64151bdc0c6aa0235192f0fc7f4badd8b0bbd6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789651"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="18585-103">ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="18585-103">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>

<span data-ttu-id="18585-104">Geçerli iş parçacığının tuttuğu kilit sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="18585-104">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="18585-105">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="18585-105">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18585-106">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="18585-106">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18585-107">Parametreler</span><span class="sxs-lookup"><span data-stu-id="18585-107">Parameters</span></span>  

 `pCount`  
 <span data-ttu-id="18585-108">dışı Geçerli iş parçacığının tuttuğu kilit sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="18585-108">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18585-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="18585-109">Requirements</span></span>  

 <span data-ttu-id="18585-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18585-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18585-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="18585-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="18585-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="18585-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="18585-113">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="18585-113">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18585-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="18585-114">See also</span></span>

- [<span data-ttu-id="18585-115">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="18585-115">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
