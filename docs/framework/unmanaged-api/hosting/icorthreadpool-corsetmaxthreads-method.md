---
title: ICorThreadpool::CorSetMaxThreads Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorSetMaxThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetMaxThreads
helpviewer_keywords:
- ICorThreadpool::CorSetMaxThreads method [.NET Framework hosting]
- CorSetMaxThreads method [.NET Framework hosting]
ms.assetid: 4a846238-df4e-4060-ba3b-5173f6a51e85
topic_type:
- apiref
ms.openlocfilehash: 7f972bcfedd028d85debbbd60968a57c4d64ee0c
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760361"
---
# <a name="icorthreadpoolcorsetmaxthreads-method"></a><span data-ttu-id="d1706-102">ICorThreadpool::CorSetMaxThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d1706-102">ICorThreadpool::CorSetMaxThreads Method</span></span>
<span data-ttu-id="d1706-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="d1706-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1706-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="d1706-104">Syntax</span></span>  
  
```cpp  
HRESULT CorSetMaxThreads (  
    [in] DWORD MaxWorkerThreads,  
    [in] DWORD MaxIOCompletionThreads  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="d1706-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d1706-105">Requirements</span></span>  
 <span data-ttu-id="d1706-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1706-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1706-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="d1706-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d1706-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="d1706-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d1706-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1706-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1706-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d1706-110">See also</span></span>

- [<span data-ttu-id="d1706-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d1706-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
