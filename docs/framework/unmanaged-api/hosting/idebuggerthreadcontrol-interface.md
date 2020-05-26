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
ms.openlocfilehash: 82c6113f4df3334500128df22f7e9ce8d4bf151f
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805288"
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="393c3-102">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="393c3-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="393c3-103">, Hata ayıklama Hizmetleri tarafından iş parçacıklarının engellenmesi ve engellemesini kaldırma hakkında bilgi için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="393c3-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="393c3-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="393c3-104">Methods</span></span>  
  
|<span data-ttu-id="393c3-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="393c3-105">Method</span></span>|<span data-ttu-id="393c3-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="393c3-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="393c3-107">ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="393c3-107">ThreadIsBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="393c3-108">Konağa, bu geri aramayı gönderen iş parçacığının hata ayıklama Hizmetleri içinde engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="393c3-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="393c3-109">ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="393c3-109">ReleaseAllRuntimeThreads Method</span></span>](idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="393c3-110">Engellenen tüm iş parçacıklarını serbest bırakmak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="393c3-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="393c3-111">StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="393c3-111">StartBlockingForDebugger Method</span></span>](idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="393c3-112">Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="393c3-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="393c3-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="393c3-113">Requirements</span></span>  
 <span data-ttu-id="393c3-114">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="393c3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="393c3-115">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="393c3-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="393c3-116">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="393c3-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="393c3-117">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="393c3-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="393c3-118">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="393c3-118">See also</span></span>

- [<span data-ttu-id="393c3-119">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="393c3-119">Hosting Interfaces</span></span>](hosting-interfaces.md)
