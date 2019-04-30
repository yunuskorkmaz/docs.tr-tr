---
title: IDebuggerThreadControl Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7a551d3cc6ab3dd3887f232018f8201de4036d1b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699662"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="d3a37-102">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d3a37-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="d3a37-103">Engelleme hakkında konak bildiren ve hata ayıklama Hizmetleri tarafından iş parçacıklarının engellemesinin kaldırılması için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="d3a37-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d3a37-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="d3a37-104">Methods</span></span>  
  
|<span data-ttu-id="d3a37-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="d3a37-105">Method</span></span>|<span data-ttu-id="d3a37-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="d3a37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d3a37-107">ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3a37-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="d3a37-108">Bu geri gönderme iş parçacığı hakkında konağa bildirir blok içinde hata ayıklama Hizmetleri için.</span><span class="sxs-lookup"><span data-stu-id="d3a37-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="d3a37-109">ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3a37-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="d3a37-110">Konak, hata ayıklama Hizmetleri engellenen tüm iş parçacıkları hakkında yayımlamayı olduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="d3a37-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="d3a37-111">StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d3a37-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="d3a37-112">Konak, hata ayıklama Hizmetleri tüm iş parçacıklarının engellemesini başlamak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="d3a37-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d3a37-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d3a37-113">Requirements</span></span>  
 <span data-ttu-id="d3a37-114">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3a37-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3a37-115">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d3a37-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d3a37-116">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d3a37-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d3a37-117">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3a37-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3a37-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="d3a37-118">See also</span></span>

- [<span data-ttu-id="d3a37-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="d3a37-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
