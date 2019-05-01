---
title: IGCThreadControl Arabirimi
ms.date: 03/30/2017
api_name:
- IGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCThreadControl
helpviewer_keywords:
- IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 3ff04d75-85ac-4df9-886d-dbaa037c0552
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5c00f401bedc1a2810c4e9b3046a45e53a79f1ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992777"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="4fe4d-102">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4fe4d-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="4fe4d-103">Bir çöp toplama işlemi için normalde engellenecek iş parçacıklarını zamanlama katılım için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="4fe4d-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4fe4d-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="4fe4d-104">Methods</span></span>  
  
|<span data-ttu-id="4fe4d-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="4fe4d-105">Method</span></span>|<span data-ttu-id="4fe4d-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="4fe4d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4fe4d-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fe4d-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="4fe4d-108">Konak, çalışma zamanı iş parçacıklarının çöp toplama ya da diğer ertelenmesi sonra sürdürülmekte bildirir.</span><span class="sxs-lookup"><span data-stu-id="4fe4d-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="4fe4d-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fe4d-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="4fe4d-110">Konak, çalışma zamanının çöp toplama için bir iş parçacığını askıya alma ya da diğer ertelenmesi başlıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="4fe4d-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="4fe4d-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4fe4d-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="4fe4d-112">Konak, çağrıyı yapan iş parçacığının yaklaşık, belki de bir çöp toplama ya da diğer ertelenmesi için engellemek için olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4fe4d-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fe4d-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4fe4d-113">Requirements</span></span>  
 <span data-ttu-id="4fe4d-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4fe4d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fe4d-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4fe4d-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4fe4d-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4fe4d-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4fe4d-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fe4d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fe4d-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4fe4d-118">See also</span></span>

- [<span data-ttu-id="4fe4d-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="4fe4d-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
