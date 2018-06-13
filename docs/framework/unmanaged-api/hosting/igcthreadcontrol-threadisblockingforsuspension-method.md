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
ms.openlocfilehash: 6f4b767fe7134833ee2e404be30bb51bf1385ec9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437043"
---
# <a name="igcthreadcontrolthreadisblockingforsuspension-method"></a><span data-ttu-id="e0baf-102">IGCThreadControl::ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e0baf-102">IGCThreadControl::ThreadIsBlockingForSuspension Method</span></span>
<span data-ttu-id="e0baf-103">Konak, çağrıyı yapan iş parçacığı hakkında belki de çöp toplama veya diğer askıya için engelle olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="e0baf-103">Notifies the host that the thread that is making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0baf-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e0baf-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForSuspension ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="e0baf-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e0baf-105">Remarks</span></span>  
 <span data-ttu-id="e0baf-106">Konak içinde tercih edebilirsiniz `ThreadIsBlockingForSuspension` geri çağırma kullanılıp bir iş parçacığı yeniden zamanlamak.</span><span class="sxs-lookup"><span data-stu-id="e0baf-106">The host may choose within the `ThreadIsBlockingForSuspension` callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0baf-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e0baf-107">Requirements</span></span>  
 <span data-ttu-id="e0baf-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0baf-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0baf-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e0baf-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e0baf-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e0baf-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e0baf-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0baf-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0baf-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="e0baf-112">See Also</span></span>  
 [<span data-ttu-id="e0baf-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e0baf-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
