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
ms.openlocfilehash: 39834ba868a21ead3113f2f0d9157cd210d9798c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721653"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="fca65-102">IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fca65-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="fca65-103">Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="fca65-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fca65-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="fca65-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="fca65-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fca65-105">Remarks</span></span>  

 <span data-ttu-id="fca65-106">Konak, `ThreadIsBlockingForSuspension` bir iş parçacığını yeniden zamanlamalı geri çağırma dahilinde seçim gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="fca65-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fca65-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fca65-107">Requirements</span></span>  

 <span data-ttu-id="fca65-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fca65-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fca65-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fca65-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fca65-110">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="fca65-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fca65-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fca65-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fca65-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fca65-112">See also</span></span>

- [<span data-ttu-id="fca65-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fca65-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
