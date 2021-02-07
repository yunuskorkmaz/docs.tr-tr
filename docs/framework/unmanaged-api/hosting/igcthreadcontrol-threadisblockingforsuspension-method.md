---
description: 'Daha fazla bilgi edinin: IGCThreadControl:: Threadıblockingforaskıya alma yöntemi'
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
ms.openlocfilehash: 13023a75ab1c438abebbeb16fd9fe7c4b95c37ab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709210"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="23e4a-103">IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="23e4a-103">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>

<span data-ttu-id="23e4a-104">Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="23e4a-104">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="23e4a-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="23e4a-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="23e4a-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="23e4a-106">Remarks</span></span>  

 <span data-ttu-id="23e4a-107">Konak, `ThreadIsBlockingForSuspension` bir iş parçacığını yeniden zamanlamalı geri çağırma dahilinde seçim gösterebilir.</span><span class="sxs-lookup"><span data-stu-id="23e4a-107">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="23e4a-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="23e4a-108">Requirements</span></span>  

 <span data-ttu-id="23e4a-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="23e4a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="23e4a-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="23e4a-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="23e4a-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="23e4a-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="23e4a-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="23e4a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e4a-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="23e4a-113">See also</span></span>

- [<span data-ttu-id="23e4a-114">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="23e4a-114">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
