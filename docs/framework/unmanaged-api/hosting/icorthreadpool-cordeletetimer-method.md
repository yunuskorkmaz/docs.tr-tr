---
title: ICorThreadpool::CorDeleteTimer Yöntemi
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorDeleteTimer
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeleteTimer
helpviewer_keywords:
- ICorThreadpool::CorDeleteTimer method [.NET Framework hosting]
- CorDeleteTimer method [.NET Framework hosting]
ms.assetid: 74847c35-7ca1-466a-b750-b25e7b03d100
topic_type:
- apiref
ms.openlocfilehash: c4ea53502c58106190a8ca5d194039dc3600af75
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/21/2020
ms.locfileid: "83760439"
---
# <a name="icorthreadpoolcordeletetimer-method"></a><span data-ttu-id="5381b-102">ICorThreadpool::CorDeleteTimer Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5381b-102">ICorThreadpool::CorDeleteTimer Method</span></span>
<span data-ttu-id="5381b-103">Bu yöntem .NET Framework altyapısını destekler ve doğrudan kodunuzdan kullanılmaya yönelik değildir.</span><span class="sxs-lookup"><span data-stu-id="5381b-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5381b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5381b-104">Syntax</span></span>  
  
```cpp  
HRESULT CorDeleteTimer (  
    [in]  HANDLE Timer,  
    [in]  HANDLE CompletionEvent,  
    [out] BOOL*  result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5381b-105">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5381b-105">Requirements</span></span>  
 <span data-ttu-id="5381b-106">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5381b-106">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5381b-107">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5381b-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5381b-108">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5381b-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5381b-109">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5381b-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5381b-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5381b-110">See also</span></span>

- [<span data-ttu-id="5381b-111">ICorThreadpool Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5381b-111">ICorThreadpool Interface</span></span>](icorthreadpool-interface.md)
