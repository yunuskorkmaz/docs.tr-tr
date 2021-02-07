---
description: 'Şu konuda daha fazla bilgi edinin: IDebuggerThreadControl arabirimi'
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
ms.openlocfilehash: 293a120d44b9b04d7e367546c477fb273f535310
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709778"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="98349-103">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98349-103">IDebuggerThreadControl Interface</span></span>

<span data-ttu-id="98349-104">, Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="98349-104">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98349-105">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="98349-105">Methods</span></span>  
  
|<span data-ttu-id="98349-106">Yöntem</span><span class="sxs-lookup"><span data-stu-id="98349-106">Method</span></span>|<span data-ttu-id="98349-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98349-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98349-108">ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98349-108">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="98349-109">Konağa, bu geri aramayı gönderen iş parçacığının hata ayıklama Hizmetleri içinde engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="98349-109">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="98349-110">ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98349-110">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="98349-111">Engellenen tüm iş parçacıklarını serbest bırakmak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="98349-111">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="98349-112">StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98349-112">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="98349-113">Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="98349-113">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98349-114">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98349-114">Requirements</span></span>  

 <span data-ttu-id="98349-115">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98349-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98349-116">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="98349-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98349-117">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="98349-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98349-118">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98349-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98349-119">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="98349-119">See also</span></span>

- [<span data-ttu-id="98349-120">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98349-120">Hosting Interfaces</span></span>](hosting-interfaces.md)
