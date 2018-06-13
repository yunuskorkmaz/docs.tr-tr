---
title: ICorConfiguration Arabirimi
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 63699f0af69b3a7623c5e9da156c2ff8ae83ccfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437530"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="98df1-102">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="98df1-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="98df1-103">Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemleri sağlar.</span><span class="sxs-lookup"><span data-stu-id="98df1-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="98df1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="98df1-104">Methods</span></span>  
  
|<span data-ttu-id="98df1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="98df1-105">Method</span></span>|<span data-ttu-id="98df1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="98df1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="98df1-107">AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98df1-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="98df1-108">Hata Ayıklama Hizmetleri belirli bir iş parçacığı hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryoları sırasında durdurulmuş bir uygulama sahipken çalıştırmaya devam etmeyi izin verilmesi gerektiğini belirtir.</span><span class="sxs-lookup"><span data-stu-id="98df1-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="98df1-109">SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98df1-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="98df1-110">CLR iş parçacığı bloke ve engeli kaldırılmış olarak hata ayıklama için hata ayıklama Hizmetleri çağıracak geri çağırma arabirimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98df1-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="98df1-111">SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98df1-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="98df1-112">Geri çağırma arabirimi sanal bellek sınırları değiştirmek için ana istemek için atık toplayıcısı tarafından kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98df1-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="98df1-113">SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="98df1-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="98df1-114">Çöp toplama için engellenmesi çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri çağırma arabirimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="98df1-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="98df1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="98df1-115">Requirements</span></span>  
 <span data-ttu-id="98df1-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98df1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98df1-117">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="98df1-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="98df1-118">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="98df1-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="98df1-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98df1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98df1-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="98df1-120">See Also</span></span>  
 [<span data-ttu-id="98df1-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="98df1-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="98df1-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="98df1-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
