---
description: 'Daha fazla bilgi edinin: IGCThreadControl arabirimi'
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
ms.openlocfilehash: 07c76848668b1525f4ff45ba5de746beefe0e004
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709291"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="71961-103">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="71961-103">IGCThreadControl Interface</span></span>

<span data-ttu-id="71961-104">Bir çöp toplama işlemi için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="71961-104">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="71961-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="71961-105">Methods</span></span>  
  
|<span data-ttu-id="71961-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="71961-106">Method</span></span>|<span data-ttu-id="71961-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="71961-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="71961-108">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71961-108">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="71961-109">Bir atık toplama ya da başka bir askıya alma işleminden sonra çalışma zamanının iş parçacıklarını sürdürüyor olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="71961-109">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="71961-110">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71961-110">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="71961-111">Bir atık toplama veya başka bir askıya alma için bir iş parçacığının askıya alınma zamanı olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="71961-111">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="71961-112">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="71961-112">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="71961-113">Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu ana bilgisayara bildirir.</span><span class="sxs-lookup"><span data-stu-id="71961-113">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="71961-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="71961-114">Requirements</span></span>  

 <span data-ttu-id="71961-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="71961-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="71961-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="71961-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="71961-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="71961-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="71961-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="71961-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71961-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="71961-119">See also</span></span>

- [<span data-ttu-id="71961-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="71961-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
