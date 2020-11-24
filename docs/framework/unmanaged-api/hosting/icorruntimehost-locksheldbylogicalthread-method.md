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
ms.openlocfilehash: 16f34d91861f9fcae51691ab13549bdf1ef333a7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95671505"
---
# <a name="icorruntimehostlocksheldbylogicalthread-method"></a><span data-ttu-id="d70ef-102">ICorRuntimeHost::LocksHeldByLogicalThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d70ef-102">ICorRuntimeHost::LocksHeldByLogicalThread Method</span></span>

<span data-ttu-id="d70ef-103">Geçerli iş parçacığının tuttuğu kilit sayısını alır.</span><span class="sxs-lookup"><span data-stu-id="d70ef-103">Retrieves the number of locks that current thread holds.</span></span>  
  
 <span data-ttu-id="d70ef-104">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="d70ef-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d70ef-105">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d70ef-105">Syntax</span></span>  
  
```cpp  
HRESULT LocksHeldByLogicalThread(  
    [out] DWORD *pCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d70ef-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d70ef-106">Parameters</span></span>  

 `pCount`  
 <span data-ttu-id="d70ef-107">dışı Geçerli iş parçacığının tuttuğu kilit sayısına yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="d70ef-107">[out] A pointer to the number of locks that the current thread holds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d70ef-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d70ef-108">Requirements</span></span>  

 <span data-ttu-id="d70ef-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d70ef-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d70ef-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d70ef-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d70ef-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="d70ef-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d70ef-112">**.NET Framework sürümleri:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="d70ef-112">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70ef-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d70ef-113">See also</span></span>

- [<span data-ttu-id="d70ef-114">ICorRuntimeHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d70ef-114">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
