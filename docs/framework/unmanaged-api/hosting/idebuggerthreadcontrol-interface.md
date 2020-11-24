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
ms.openlocfilehash: 2268fce5d3ca732d852edfdb6f0edf63117df363
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684219"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="17075-102">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="17075-102">IDebuggerThreadControl Interface</span></span>

<span data-ttu-id="17075-103">, Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="17075-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="17075-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="17075-104">Methods</span></span>  
  
|<span data-ttu-id="17075-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="17075-105">Method</span></span>|<span data-ttu-id="17075-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="17075-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="17075-107">ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17075-107">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="17075-108">Konağa, bu geri aramayı gönderen iş parçacığının hata ayıklama Hizmetleri içinde engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="17075-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="17075-109">ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17075-109">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="17075-110">Engellenen tüm iş parçacıklarını serbest bırakmak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="17075-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="17075-111">StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="17075-111">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="17075-112">Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="17075-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="17075-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="17075-113">Requirements</span></span>  

 <span data-ttu-id="17075-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17075-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17075-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17075-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17075-116">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="17075-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17075-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17075-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17075-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="17075-118">See also</span></span>

- [<span data-ttu-id="17075-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="17075-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
