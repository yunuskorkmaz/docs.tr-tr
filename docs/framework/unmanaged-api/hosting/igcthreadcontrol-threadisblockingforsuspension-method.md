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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aa2872fec7765f38fba9589a6fab659e73131937
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620467"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="70366-102">IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="70366-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="70366-103">Konak, çağrıyı yapan iş parçacığının yaklaşık, belki de bir çöp toplama ya da diğer ertelenmesi için engellemek için olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="70366-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70366-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="70366-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="70366-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="70366-105">Remarks</span></span>  
 <span data-ttu-id="70366-106">Konak içinde tercih edebilirsiniz `ThreadIsBlockingForSuspension` geri çağırma kullanılıp bir iş parçacığı yeniden zamanlamak.</span><span class="sxs-lookup"><span data-stu-id="70366-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70366-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="70366-107">Requirements</span></span>  
 <span data-ttu-id="70366-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70366-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70366-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="70366-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70366-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="70366-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70366-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70366-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70366-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="70366-112">See also</span></span>
- [<span data-ttu-id="70366-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="70366-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
