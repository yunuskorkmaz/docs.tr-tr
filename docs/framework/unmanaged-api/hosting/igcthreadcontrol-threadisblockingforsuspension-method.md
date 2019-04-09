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
ms.openlocfilehash: 7cd6c1dff30bce8857b9fb4092670667109932c3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094092"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="cf3ab-102">IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cf3ab-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="cf3ab-103">Konak, çağrıyı yapan iş parçacığının yaklaşık, belki de bir çöp toplama ya da diğer ertelenmesi için engellemek için olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="cf3ab-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cf3ab-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="cf3ab-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cf3ab-105">Remarks</span></span>  
 <span data-ttu-id="cf3ab-106">Konak içinde tercih edebilirsiniz `ThreadIsBlockingForSuspension` geri çağırma kullanılıp bir iş parçacığı yeniden zamanlamak.</span><span class="sxs-lookup"><span data-stu-id="cf3ab-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf3ab-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cf3ab-107">Requirements</span></span>  
 <span data-ttu-id="cf3ab-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf3ab-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf3ab-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="cf3ab-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cf3ab-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="cf3ab-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="cf3ab-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="cf3ab-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cf3ab-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cf3ab-112">See also</span></span>

- [<span data-ttu-id="cf3ab-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cf3ab-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
