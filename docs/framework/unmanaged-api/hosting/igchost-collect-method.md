---
title: IGCHost::Collect Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHost.Collect
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- Collect
helpviewer_keywords:
- Collect method, IGCHost interface [.NET Framework hosting]
- IGCHost::Collect method [.NET Framework hosting]
ms.assetid: fc7d9448-3186-494d-9f0d-ea39717e9a82
topic_type:
- apiref
ms.openlocfilehash: f32b91f0d47449f80c38542162035999d616813b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670153"
---
# <a name="igchostcollect-method"></a><span data-ttu-id="af6a4-102">IGCHost::Collect Yöntemi</span><span class="sxs-lookup"><span data-stu-id="af6a4-102">IGCHost::Collect Method</span></span>

<span data-ttu-id="af6a4-103">Geçerli çöp toplamanın durumundan bağımsız olarak, belirli bir oluşturma için bir koleksiyonu meydana gelecek şekilde zorlar.</span><span class="sxs-lookup"><span data-stu-id="af6a4-103">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af6a4-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="af6a4-104">Syntax</span></span>  
  
```cpp  
HRESULT Collect (  
    [in] LONG Generation  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="af6a4-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="af6a4-105">Parameters</span></span>  

 `Generation`  
 <span data-ttu-id="af6a4-106">'ndaki Çöp toplamanın gerçekleştirileceği oluşturma.</span><span class="sxs-lookup"><span data-stu-id="af6a4-106">[in] The generation on which to perform the garbage collection.</span></span> <span data-ttu-id="af6a4-107">-1 değeri, tüm nesiller 'in çöp toplama işlemini üstlendiridiğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="af6a4-107">A value of -1 indicates that all generations will undergo a garbage collection.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="af6a4-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="af6a4-108">Requirements</span></span>  

 <span data-ttu-id="af6a4-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="af6a4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="af6a4-110">**Üst bilgi:** GCHost. IDL, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="af6a4-110">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="af6a4-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="af6a4-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="af6a4-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="af6a4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af6a4-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="af6a4-113">See also</span></span>

- [<span data-ttu-id="af6a4-114">IGCHost Arabirimi</span><span class="sxs-lookup"><span data-stu-id="af6a4-114">IGCHost Interface</span></span>](igchost-interface.md)
