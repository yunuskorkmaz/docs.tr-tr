---
description: 'Şu konuda daha fazla bilgi edinin: IDebuggerThreadControl:: ReleaseAllRuntimeThreads yöntemi'
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
ms.openlocfilehash: bf551ccc2ae5bde3333dc8e3957099590a494dd3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709795"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="b3970-103">IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b3970-103">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>

<span data-ttu-id="b3970-104">Engellenen tüm iş parçacıklarını serbest bırakmak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="b3970-104">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3970-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b3970-105">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b3970-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b3970-106">Remarks</span></span>  

 <span data-ttu-id="b3970-107">`ReleaseAllRuntimeThreads`Yöntemi bir çalışma zamanı iş parçacığında hiçbir şekilde çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="b3970-107">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="b3970-108">Konakta engellenen bir çalışma zamanı iş parçacığı varsa, şimdi onu serbest bırakmalıdır.</span><span class="sxs-lookup"><span data-stu-id="b3970-108">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3970-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b3970-109">Requirements</span></span>  

 <span data-ttu-id="b3970-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3970-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3970-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b3970-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b3970-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b3970-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b3970-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3970-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3970-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b3970-114">See also</span></span>

- [<span data-ttu-id="b3970-115">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b3970-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
