---
description: 'Hakkında daha fazla bilgi edinin: IGCHostControl:: RequestVirtualMemLimit Yöntemi'
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
ms.openlocfilehash: b0ee22671b63be0ed0d23ebb103a6a5a7ca9f2b9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709431"
---
# <a name="igchostcontrolrequestvirtualmemlimit-method"></a><span data-ttu-id="6cec0-103">IGCHostControl::RequestVirtualMemLimit Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6cec0-103">IGCHostControl::RequestVirtualMemLimit Method</span></span>

<span data-ttu-id="6cec0-104">Konağı, sanal bellek sınırlarını değiştirecek şekilde ister.</span><span class="sxs-lookup"><span data-stu-id="6cec0-104">Requests the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6cec0-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6cec0-105">Syntax</span></span>  
  
```cpp  
HRESULT RequestVirtualMemLimit (  
    [in] SIZE_T       sztMaxVirtualMemMB,  
    [in, out] SIZE_T* psztNewMaxVirtualMemMB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6cec0-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6cec0-106">Parameters</span></span>  

 `sztMaxVirtualMemMB`  
 <span data-ttu-id="6cec0-107">'ndaki Ayrılacak belleğin istenen boyutu.</span><span class="sxs-lookup"><span data-stu-id="6cec0-107">[in] The requested size of memory to be allocated.</span></span>  
  
 `psztNewMaxVirtualMemMB`  
 <span data-ttu-id="6cec0-108">[in, out] Ayrılan belleğin gerçek boyutuna yönelik bir işaretçi.</span><span class="sxs-lookup"><span data-stu-id="6cec0-108">[in, out] A pointer to the actual size of memory allocated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6cec0-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6cec0-109">Requirements</span></span>  

 <span data-ttu-id="6cec0-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6cec0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6cec0-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6cec0-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6cec0-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="6cec0-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6cec0-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6cec0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cec0-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6cec0-114">See also</span></span>

- [<span data-ttu-id="6cec0-115">IGCHostControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6cec0-115">IGCHostControl Interface</span></span>](igchostcontrol-interface.md)
