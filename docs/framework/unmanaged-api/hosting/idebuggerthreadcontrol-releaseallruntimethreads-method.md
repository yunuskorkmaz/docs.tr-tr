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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699870"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="a1572-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="a1572-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="a1572-103">Konak, hata ayıklama Hizmetleri engellenen tüm iş parçacıkları hakkında yayımlamayı olduğunu size bildirir.</span><span class="sxs-lookup"><span data-stu-id="a1572-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1572-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="a1572-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="a1572-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="a1572-105">Remarks</span></span>  
 <span data-ttu-id="a1572-106">`ReleaseAllRuntimeThreads` Yöntemi bir çalışma zamanı iş parçacığı üzerinde hiçbir zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="a1572-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="a1572-107">Ana bilgisayarın bir çalışma zamanı iş parçacığı engellendi varsa, bunu şimdi serbest.</span><span class="sxs-lookup"><span data-stu-id="a1572-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1572-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="a1572-108">Requirements</span></span>  
 <span data-ttu-id="a1572-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1572-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1572-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a1572-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a1572-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="a1572-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a1572-112">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1572-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1572-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="a1572-113">See also</span></span>

- [<span data-ttu-id="a1572-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="a1572-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
