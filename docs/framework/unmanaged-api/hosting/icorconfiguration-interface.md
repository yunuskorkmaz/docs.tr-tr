---
title: ICorConfiguration Arabirimi
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
- ICorConfiguration
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorConfiguration
helpviewer_keywords:
- ICorConfiguration interface [.NET Framework hosting]
ms.assetid: aaf96116-372b-4538-afb1-9e0fcdac1f98
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: af9a7d4bb1d38fd4a81e954074b074325409ee5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="f4b87-102">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f4b87-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="f4b87-103">Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="f4b87-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f4b87-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="f4b87-104">Methods</span></span>  
  
|<span data-ttu-id="f4b87-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="f4b87-105">Method</span></span>|<span data-ttu-id="f4b87-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="f4b87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f4b87-107">AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4b87-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="f4b87-108">Hata Ayıklama Hizmetleri belirli bir iş parçacığı hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryoları sırasında durdurulmuş bir uygulama sahipken çalıştırmaya devam etmeyi izin verilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="f4b87-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="f4b87-109">SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4b87-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="f4b87-110">CLR iş parçacığı bloke ve engeli kaldırılmış olarak hata ayıklama için hata ayıklama Hizmetleri çağıracak geri çağırma arabirimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f4b87-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="f4b87-111">SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4b87-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="f4b87-112">Geri çağırma arabirimi sanal bellek sınırları değiştirmek için ana istemek için atık toplayıcısı tarafından kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f4b87-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="f4b87-113">SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f4b87-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="f4b87-114">Çöp toplama için engellenmesi çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri çağırma arabirimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="f4b87-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f4b87-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f4b87-115">Requirements</span></span>  
 <span data-ttu-id="f4b87-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4b87-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4b87-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="f4b87-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4b87-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="f4b87-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4b87-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4b87-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4b87-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="f4b87-120">See Also</span></span>  
 [<span data-ttu-id="f4b87-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="f4b87-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="f4b87-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="f4b87-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
