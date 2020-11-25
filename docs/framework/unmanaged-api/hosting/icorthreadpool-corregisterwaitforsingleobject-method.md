---
title: ICorThreadpool::CorRegisterWaitForSingleObject Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorRegisterWaitForSingleObject
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRegisterWaitForSingleObject
helpviewer_keywords:
- ICorThreadpool::CorRegisterWaitForSingleObject method [.NET Framework hosting]
- CorRegisterWaitForSingleObject method [.NET Framework hosting]
ms.assetid: cade1feb-71d2-43ed-85ca-7b2e9da12994
topic_type:
- apiref
ms.openlocfilehash: 9f555d3119ede5eabe61467aa81d35aa5c354751
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727854"
---
# <a name="icorthreadpoolcorregisterwaitforsingleobject-method"></a><span data-ttu-id="a6971-102">ICorThreadpool::CorRegisterWaitForSingleObject Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a6971-102">ICorThreadpool::CorRegisterWaitForSingleObject Method</span></span>

<span data-ttu-id="a6971-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="a6971-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6971-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="a6971-104">Syntax</span></span>  
  
```cpp  
HRESULT CorRegisterWaitForSingleObject (  
    [in]  HANDLE*             phNewWaitObject,  
    [in]  HANDLE              hWaitObject,  
    [in]  WAITORTIMERCALLBACK Callback,  
    [in]  PVOID               Context,  
    [in]  ULONG               timeout,  
    [in]  BOOL                executeOnlyOnce,  
    [out] BOOL*               result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="a6971-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a6971-105">Requirements</span></span>  

 <span data-ttu-id="a6971-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6971-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6971-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a6971-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a6971-108">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="a6971-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a6971-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6971-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6971-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a6971-110">See also</span></span>

- [<span data-ttu-id="a6971-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a6971-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
