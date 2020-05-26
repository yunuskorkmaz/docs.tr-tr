---
title: IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi
ms.date: 03/30/2017
api_name:
- IGCThreadControl.ThreadIsBlockingForSuspension
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForSuspension
helpviewer_keywords:
- IGCThreadControl::ThreadIsBlockingForSuspension method [.NET Framework hosting]
- ThreadIsBlockingForSuspension method [.NET Framework hosting]
ms.assetid: ed5b5b58-7db7-46b5-9e2c-278db7159cee
topic_type:
- apiref
ms.openlocfilehash: b5f6d7d40274972438a01313bc6aaec475b8e0c6
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805085"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="6126d-102">IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6126d-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="6126d-103">Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="6126d-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6126d-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="6126d-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="6126d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6126d-105">Remarks</span></span>  
 <span data-ttu-id="6126d-106">Konak, `ThreadIsBlockingForSuspension` bir iş parçacığını yeniden zamanlamalı geri çağırma dahilinde seçim gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="6126d-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6126d-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6126d-107">Requirements</span></span>  
 <span data-ttu-id="6126d-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6126d-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6126d-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6126d-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6126d-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="6126d-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6126d-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6126d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6126d-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="6126d-112">See also</span></span>

- [<span data-ttu-id="6126d-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6126d-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
