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
ms.openlocfilehash: 9296aedf24979624c3d7357a4d51be835716a16f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438034"
---
# <a name="igcthreadcontrol-interface"></a><span data-ttu-id="f5691-102">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f5691-102">IGCThreadControl Interface</span></span>
<span data-ttu-id="f5691-103">Çöp toplama için engellenmesi iş parçacıklarını zamanlama içinde katılan için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f5691-103">Provides methods for participating in the scheduling of threads that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f5691-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f5691-104">Methods</span></span>  
  
|<span data-ttu-id="f5691-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f5691-105">Method</span></span>|<span data-ttu-id="f5691-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f5691-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f5691-107">SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5691-107">SuspensionEnding Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionending-method.md)|<span data-ttu-id="f5691-108">Konak bir atık toplama veya diğer askıya sonra çalışma zamanı iş parçacıklarını sürdürme olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f5691-108">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="f5691-109">SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5691-109">SuspensionStarting Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-suspensionstarting-method.md)|<span data-ttu-id="f5691-110">Ana bilgisayar, çalışma zamanı modülü çöp toplama için bir iş parçacığı askıya alınması veya diğer askıya başlıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="f5691-110">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>|  
|[<span data-ttu-id="f5691-111">ThreadIsBlockingForSuspension Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f5691-111">ThreadIsBlockingForSuspension Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md)|<span data-ttu-id="f5691-112">Konak, çağrıyı yapan iş parçacığı hakkında belki de çöp toplama veya diğer askıya için engelle olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f5691-112">Notifies the host that the thread making the call is about to block, perhaps for a garbage collection or other suspension.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f5691-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f5691-113">Requirements</span></span>  
 <span data-ttu-id="f5691-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5691-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5691-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f5691-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f5691-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f5691-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5691-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5691-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5691-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f5691-118">See Also</span></span>  
 [<span data-ttu-id="f5691-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f5691-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
