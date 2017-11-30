---
title: IDebuggerThreadControl Arabirimi
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: IDebuggerThreadControl
helpviewer_keywords: IDebuggerThreadControl interface [.NET Framework hosting]
ms.assetid: 0a270c42-a7d1-45f1-a64d-fa3e84d14532
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7e3f8d04a47607958ff5d439b501a6de9bbc5b02
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrol-interface"></a><span data-ttu-id="1f568-102">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1f568-102">IDebuggerThreadControl Interface</span></span>
<span data-ttu-id="1f568-103">Engelleme hakkında konak bildirme ve hata ayıklama Hizmetleri tarafından iş parçacıklarının kaldırma için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="1f568-103">Provides methods for notifying the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f568-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="1f568-104">Methods</span></span>  
  
|<span data-ttu-id="1f568-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="1f568-105">Method</span></span>|<span data-ttu-id="1f568-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="1f568-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f568-107">Threadısblockingfordebugger yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f568-107">ThreadIsBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-threadisblockingfordebugger-method.md)|<span data-ttu-id="1f568-108">Bu geri çağırma gönderme iş parçacığı hakkındadır konak bildirir hata ayıklama Hizmetleri blokta için.</span><span class="sxs-lookup"><span data-stu-id="1f568-108">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>|  
|[<span data-ttu-id="1f568-109">ReleaseAllRuntimeThreads yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f568-109">ReleaseAllRuntimeThreads Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-releaseallruntimethreads-method.md)|<span data-ttu-id="1f568-110">Ana bilgisayar hata ayıklama hizmetleri hakkında engellenmiş durumda olan tüm iş parçacıklarının yayın olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1f568-110">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>|  
|[<span data-ttu-id="1f568-111">StartBlockingForDebugger yöntemi</span><span class="sxs-lookup"><span data-stu-id="1f568-111">StartBlockingForDebugger Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-startblockingfordebugger-method.md)|<span data-ttu-id="1f568-112">Ana bilgisayar hata ayıklama hizmetleri hakkında tüm iş parçacıklarının engelleme başlangıç olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="1f568-112">Notifies the host that the debugging services are about to start blocking all threads.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f568-113">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1f568-113">Requirements</span></span>  
 <span data-ttu-id="1f568-114">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f568-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f568-115">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1f568-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1f568-116">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1f568-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1f568-117">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f568-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f568-118">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1f568-118">See Also</span></span>  
 [<span data-ttu-id="1f568-119">Barındırma arabirimleri</span><span class="sxs-lookup"><span data-stu-id="1f568-119">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
