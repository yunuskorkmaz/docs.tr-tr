---
title: "IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ReleaseAllRuntimeThreads
api_location: mscoree.dll
api_type: COM
f1_keywords: ReleaseAllRuntimeThreads
helpviewer_keywords:
- ReleaseAllRuntimeThreads method [.NET Framework hosting]
- IDebuggerThreadControl::ReleaseAllRuntimeThreads method [.NET Framework hosting]
ms.assetid: 1a2995ff-5f02-4b49-84dc-3a5f9cfd7d55
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e6e2c4032a0765083177df9a6d7d5206448f566
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="20649-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="20649-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="20649-103">Ana bilgisayar hata ayıklama hizmetleri hakkında engellenmiş durumda olan tüm iş parçacıklarının yayın olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="20649-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20649-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="20649-104">Syntax</span></span>  
  
```  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="20649-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="20649-105">Remarks</span></span>  
 <span data-ttu-id="20649-106">`ReleaseAllRuntimeThreads` Yöntemi bir çalışma zamanı iş parçacığı üzerinde hiçbir zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="20649-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="20649-107">Engellenen bir çalışma zamanı iş parçacığı ana bilgisayar varsa, bunu şimdi serbest.</span><span class="sxs-lookup"><span data-stu-id="20649-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20649-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="20649-108">Requirements</span></span>  
 <span data-ttu-id="20649-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="20649-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="20649-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="20649-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="20649-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="20649-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="20649-112">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="20649-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20649-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="20649-113">See Also</span></span>  
 [<span data-ttu-id="20649-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="20649-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
