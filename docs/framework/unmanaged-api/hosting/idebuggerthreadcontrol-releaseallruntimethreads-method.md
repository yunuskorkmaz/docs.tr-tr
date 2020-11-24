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
ms.openlocfilehash: 490648ab8883b1dba257b82c0d0fa3c8e4783814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684167"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="e7a96-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e7a96-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>

<span data-ttu-id="e7a96-103">Engellenen tüm iş parçacıklarını serbest bırakmak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="e7a96-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7a96-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7a96-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="e7a96-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e7a96-105">Remarks</span></span>  

 <span data-ttu-id="e7a96-106">`ReleaseAllRuntimeThreads`Yöntemi bir çalışma zamanı iş parçacığında hiçbir şekilde çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="e7a96-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="e7a96-107">Konakta engellenen bir çalışma zamanı iş parçacığı varsa, şimdi onu serbest bırakmalıdır.</span><span class="sxs-lookup"><span data-stu-id="e7a96-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7a96-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e7a96-108">Requirements</span></span>  

 <span data-ttu-id="e7a96-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e7a96-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e7a96-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="e7a96-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e7a96-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="e7a96-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e7a96-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e7a96-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7a96-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e7a96-113">See also</span></span>

- [<span data-ttu-id="e7a96-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e7a96-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
