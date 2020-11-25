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
ms.openlocfilehash: 02facbb0ff1c0f8978d4f4f720ab370f70f07fe2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721692"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="2c146-102">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2c146-102">IGCThreadControl Interface</span></span>

<span data-ttu-id="2c146-103">Bir çöp toplama işlemi için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="2c146-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2c146-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="2c146-104">Methods</span></span>  
  
|<span data-ttu-id="2c146-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="2c146-105">Method</span></span>|<span data-ttu-id="2c146-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="2c146-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2c146-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c146-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="2c146-108">Bir atık toplama ya da başka bir askıya alma işleminden sonra çalışma zamanının iş parçacıklarını sürdürüyor olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c146-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="2c146-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c146-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="2c146-110">Bir atık toplama veya başka bir askıya alma için bir iş parçacığının askıya alınma zamanı olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c146-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="2c146-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2c146-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="2c146-112">Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu ana bilgisayara bildirir.</span><span class="sxs-lookup"><span data-stu-id="2c146-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c146-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2c146-113">Requirements</span></span>  

 <span data-ttu-id="2c146-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c146-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c146-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2c146-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2c146-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="2c146-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2c146-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c146-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c146-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="2c146-118">See also</span></span>

- [<span data-ttu-id="2c146-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="2c146-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
