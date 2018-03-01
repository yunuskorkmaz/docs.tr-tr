---
title: IDebuggerThreadControl Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IDebuggerThreadControl
helpviewer_keywords:
- IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 297a66f9466b00dec4d32f7d8a6e2bd13b6e5655
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="610a1-102">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="610a1-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="610a1-103">Engelleme hakkında konak bildirme ve hata ayıklama Hizmetleri tarafından iş parçacıklarının kaldırma için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="610a1-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="610a1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="610a1-104">Methods</span></span>  
  
|<span data-ttu-id="610a1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="610a1-105">Method</span></span>|<span data-ttu-id="610a1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="610a1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="610a1-107">ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="610a1-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="610a1-108">Bu geri çağırma gönderme iş parçacığı hakkındadır konak bildirir hata ayıklama Hizmetleri blokta için.</span><span class="sxs-lookup"><span data-stu-id="610a1-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="610a1-109">ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="610a1-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="610a1-110">Ana bilgisayar hata ayıklama hizmetleri hakkında engellenmiş durumda olan tüm iş parçacıklarının yayın olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="610a1-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="610a1-111">StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="610a1-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="610a1-112">Ana bilgisayar hata ayıklama hizmetleri hakkında tüm iş parçacıklarının engelleme başlangıç olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="610a1-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="610a1-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="610a1-113">Requirements</span></span>  
 <span data-ttu-id="610a1-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="610a1-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="610a1-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="610a1-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="610a1-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="610a1-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="610a1-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="610a1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="610a1-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="610a1-118">See Also</span></span>  
 [<span data-ttu-id="610a1-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="610a1-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
