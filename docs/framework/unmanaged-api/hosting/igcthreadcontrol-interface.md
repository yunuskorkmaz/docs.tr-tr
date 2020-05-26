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
ms.openlocfilehash: 78e667acf1573769a1a67b4c964d7801f11838fe
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805122"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="e77fb-102">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e77fb-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="e77fb-103">Bir çöp toplama işlemi için engellenebilecek iş parçacıklarının zamanlamaya katılmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="e77fb-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e77fb-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="e77fb-104">Methods</span></span>  
  
|<span data-ttu-id="e77fb-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="e77fb-105">Method</span></span>|<span data-ttu-id="e77fb-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="e77fb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e77fb-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e77fb-107">SuspensionEnding Method</span></span>](igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="e77fb-108">Bir atık toplama ya da başka bir askıya alma işleminden sonra çalışma zamanının iş parçacıklarını sürdürüyor olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="e77fb-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="e77fb-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e77fb-109">SuspensionStarting Method</span></span>](igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="e77fb-110">Bir atık toplama veya başka bir askıya alma için bir iş parçacığının askıya alınma zamanı olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="e77fb-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="e77fb-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e77fb-111">ThreadIsBlockingForSuspension Method</span></span>](igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="e77fb-112">Bir atık toplama ya da başka bir askıya alma için, çağrıyı yapan iş parçacığının engellemek üzere olduğunu ana bilgisayara bildirir.</span><span class="sxs-lookup"><span data-stu-id="e77fb-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e77fb-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e77fb-113">Requirements</span></span>  
 <span data-ttu-id="e77fb-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e77fb-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e77fb-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e77fb-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e77fb-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="e77fb-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e77fb-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e77fb-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e77fb-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e77fb-118">See also</span></span>

- [<span data-ttu-id="e77fb-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="e77fb-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
