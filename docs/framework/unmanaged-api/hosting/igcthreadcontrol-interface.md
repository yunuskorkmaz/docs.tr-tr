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
ms.openlocfilehash: 3aba31f60af25144b9f01aa9ca8cc633d4c1a438
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134795"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="aec13-102">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="aec13-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="aec13-103">Bir çöp toplama işlemi için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="aec13-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="aec13-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="aec13-104">Methods</span></span>  
  
|<span data-ttu-id="aec13-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="aec13-105">Method</span></span>|<span data-ttu-id="aec13-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="aec13-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="aec13-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aec13-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="aec13-108">Bir atık toplama ya da başka bir askıya alma işleminden sonra çalışma zamanının iş parçacıklarını sürdürüyor olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="aec13-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="aec13-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aec13-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="aec13-110">Bir atık toplama veya başka bir askıya alma için bir iş parçacığının askıya alınma zamanı olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="aec13-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="aec13-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="aec13-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="aec13-112">Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu ana bilgisayara bildirir.</span><span class="sxs-lookup"><span data-stu-id="aec13-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="aec13-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="aec13-113">Requirements</span></span>  
 <span data-ttu-id="aec13-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aec13-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aec13-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="aec13-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="aec13-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="aec13-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="aec13-117">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aec13-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aec13-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aec13-118">See also</span></span>

- [<span data-ttu-id="aec13-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="aec13-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
