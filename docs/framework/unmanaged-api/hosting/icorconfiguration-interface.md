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
ms.openlocfilehash: 80bb68486e555d6c96cf8ee56ed6d60e41c7c5c6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127810"
---
# <a name="icorconfiguration-interface"></a><span data-ttu-id="162e1-102">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="162e1-102">ICorConfiguration Interface</span></span>
<span data-ttu-id="162e1-103">Ortak dil çalışma zamanını (CLR) yapılandırmak için yöntemler sağlar.</span><span class="sxs-lookup"><span data-stu-id="162e1-103">Provides methods for configuring the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="162e1-104">Yöntemler</span><span class="sxs-lookup"><span data-stu-id="162e1-104">Methods</span></span>  
  
|<span data-ttu-id="162e1-105">Yöntem</span><span class="sxs-lookup"><span data-stu-id="162e1-105">Method</span></span>|<span data-ttu-id="162e1-106">Açıklama</span><span class="sxs-lookup"><span data-stu-id="162e1-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="162e1-107">AddDebuggerSpecialThread Yöntemi</span><span class="sxs-lookup"><span data-stu-id="162e1-107">AddDebuggerSpecialThread Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-adddebuggerspecialthread-method.md)|<span data-ttu-id="162e1-108">Hata ayıklayıcı yönetilen veya yönetilmeyen hata ayıklama senaryolarında durdurulan bir uygulamaya sahip olsa da, belirli bir iş parçacığının yürütmeye devam etmesine izin verilmesi gerektiğini hata ayıklama hizmetlerine bildirir.</span><span class="sxs-lookup"><span data-stu-id="162e1-108">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>|  
|[<span data-ttu-id="162e1-109">SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="162e1-109">SetDebuggerThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setdebuggerthreadcontrol-method.md)|<span data-ttu-id="162e1-110">Hata ayıklama Hizmetleri, CLR iş parçacıkları engellenen ve hata ayıklama için engellenmemiş olarak çağralacak geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="162e1-110">Sets the callback interface that the debugging services will call as CLR threads are blocked and unblocked for debugging.</span></span>|  
|[<span data-ttu-id="162e1-111">SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="162e1-111">SetGCHostControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgchostcontrol-method.md)|<span data-ttu-id="162e1-112">Sanal bellek sınırlarını değiştirmek üzere Konağı istemek için çöp toplayıcı tarafından kullanılacak geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="162e1-112">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>|  
|[<span data-ttu-id="162e1-113">SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="162e1-113">SetGCThreadControl Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-setgcthreadcontrol-method.md)|<span data-ttu-id="162e1-114">Bir çöp toplama işlemi için engellenmeyen çalışma zamanı olmayan görevler için iş parçacıkları zamanlama için geri çağırma arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="162e1-114">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="162e1-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="162e1-115">Requirements</span></span>  
 <span data-ttu-id="162e1-116">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="162e1-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="162e1-117">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="162e1-117">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="162e1-118">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="162e1-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="162e1-119">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="162e1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162e1-120">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="162e1-120">See also</span></span>

- [<span data-ttu-id="162e1-121">Barındırma Arabirimleri</span><span class="sxs-lookup"><span data-stu-id="162e1-121">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="162e1-122">CorRuntimeHost Coclass</span><span class="sxs-lookup"><span data-stu-id="162e1-122">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)
