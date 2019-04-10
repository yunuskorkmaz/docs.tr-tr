---
title: IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 136dab5c05c310d85a5e18bcdc6da0de901d3ace
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59227476"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="9015d-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9015d-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="9015d-103">Konak, hata ayıklama Hizmetleri engellenen tüm iş parçacıkları hakkında yayımlamayı olduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="9015d-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9015d-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9015d-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="9015d-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="9015d-105">Remarks</span></span>  
 <span data-ttu-id="9015d-106">`ReleaseAllRuntimeThreads` Yöntemi bir çalışma zamanı iş parçacığı üzerinde hiçbir zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="9015d-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="9015d-107">Ana bilgisayarın bir çalışma zamanı iş parçacığı engellendi varsa, bunu şimdi serbest.</span><span class="sxs-lookup"><span data-stu-id="9015d-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9015d-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9015d-108">Requirements</span></span>  
 <span data-ttu-id="9015d-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9015d-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9015d-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9015d-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9015d-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9015d-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9015d-112">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="9015d-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9015d-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9015d-113">See also</span></span>

- [<span data-ttu-id="9015d-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9015d-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
