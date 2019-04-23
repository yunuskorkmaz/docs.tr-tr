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
ms.openlocfilehash: b24e278b3449d0e17377495cef0f445c1ebed734
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149818"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="179c8-102">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="179c8-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="179c8-103">Ortak dil çalışma zamanı (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="179c8-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="179c8-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="179c8-104">Methods</span></span>  
  
|<span data-ttu-id="179c8-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="179c8-105">Method</span></span>|<span data-ttu-id="179c8-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="179c8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="179c8-107">AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="179c8-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="179c8-108">Hata Ayıklama Hizmetleri için hata ayıklayıcı durduruldu sırasında yönetilen veya yönetilmeyen hata ayıklama senaryoları uygulama varken yürütme devam etmek için belirli bir iş parçacığına izin verileceğini gösterir.</span><span class="sxs-lookup"><span data-stu-id="179c8-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="179c8-109">SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="179c8-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="179c8-110">CLR iş parçacığı engellenir ve engeli kaldırılmış, hata ayıklama için hata ayıklama Hizmetleri çağıran bir geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="179c8-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="179c8-111">SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="179c8-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="179c8-112">Sanal bellek sınırlarını değiştirmek için ana istemek için atık toplayıcı tarafından kullanılmak üzere geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="179c8-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="179c8-113">SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="179c8-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="179c8-114">Bir çöp toplama işlemi için normalde engellenecek çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="179c8-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="179c8-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="179c8-115">Requirements</span></span>  
 <span data-ttu-id="179c8-116">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="179c8-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="179c8-117">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="179c8-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="179c8-118">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="179c8-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="179c8-119">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="179c8-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179c8-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="179c8-120">See also</span></span>

- [<span data-ttu-id="179c8-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="179c8-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="179c8-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="179c8-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
