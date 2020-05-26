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
ms.openlocfilehash: d4814e44b1a5311cf6800c804df7a7e11000cbab
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805145"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="e2ef5-102">IGCHostControl::RequestVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e2ef5-102">IGCHostControl::RequestVirtualMemLimit Method</span></span>
<span data-ttu-id="e2ef5-103">Konağı, sanal bellek sınırlarını değiştirecek şekilde ister.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-103">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2ef5-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="e2ef5-104">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2ef5-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="e2ef5-105">Parameters</span></span>  
 `sztMaxVirtualMemMB`  
 <span data-ttu-id="e2ef5-106">'ndaki Ayrılacak belleğin istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-106">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="e2ef5-107">[in, out] Ayrılan belleğin gerçek boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-107">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2ef5-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e2ef5-108">Requirements</span></span>  
 <span data-ttu-id="e2ef5-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2ef5-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2ef5-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e2ef5-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e2ef5-111">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e2ef5-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e2ef5-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e2ef5-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2ef5-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e2ef5-113">See also</span></span>

- [<span data-ttu-id="e2ef5-114">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e2ef5-114">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
