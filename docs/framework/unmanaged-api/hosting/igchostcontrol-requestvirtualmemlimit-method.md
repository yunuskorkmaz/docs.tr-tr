---
title: IGCHostControl::RequestVirtualMemLimit Yöntemi
ms.date: 03/30/2017
api_name:
- IGCHostControl.RequestVirtualMemLimit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- RequestVirtualMemLimit
helpviewer_keywords:
- IGCHostControl::RequestVirtualMemLimit method [.NET Framework hosting]
- RequestVirtualMemLimit method [.NET Framework hosting]
ms.assetid: f4984a8c-4c0e-4460-9aa1-d022b3621228
topic_type:
- apiref
ms.openlocfilehash: bbcabdec45945b969230a40b85a62e24e323ccc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733938"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="ac1a3-102">IGCHostControl::RequestVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ac1a3-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>

<span data-ttu-id="ac1a3-103">Konağı, sanal bellek sınırlarını değiştirecek şekilde ister.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac1a3-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="ac1a3-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ac1a3-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ac1a3-105">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="ac1a3-106">'ndaki Ayrılacak belleğin istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="ac1a3-107">[in, out] Ayrılan belleğin gerçek boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ac1a3-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ac1a3-108">Requirements</span></span>  

 <span data-ttu-id="ac1a3-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ac1a3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ac1a3-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ac1a3-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ac1a3-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="ac1a3-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ac1a3-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ac1a3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1a3-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="ac1a3-113">See also</span></span>

- [<span data-ttu-id="ac1a3-114">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ac1a3-114">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
