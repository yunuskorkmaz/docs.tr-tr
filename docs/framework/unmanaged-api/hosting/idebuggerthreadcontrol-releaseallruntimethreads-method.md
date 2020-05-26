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
ms.openlocfilehash: 50ffb33456f942a71089f9bc44daa07f6b77ab21
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805293"
---
# <a name="idebuggerthreadcontrolreleaseallruntimethreads-method"></a><span data-ttu-id="126f6-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Yöntemi</span><span class="sxs-lookup"><span data-stu-id="126f6-102">IDebuggerThreadControl::ReleaseAllRuntimeThreads Method</span></span>
<span data-ttu-id="126f6-103">Engellenen tüm iş parçacıklarını serbest bırakmak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="126f6-103">Notifies the host that the debugging services are about to release all threads that are blocked.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="126f6-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="126f6-104">Syntax</span></span>  
  
```cpp  
HRESULT ReleaseAllRuntimeThreads ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="126f6-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="126f6-105">Remarks</span></span>  
 <span data-ttu-id="126f6-106">`ReleaseAllRuntimeThreads`Yöntemi bir çalışma zamanı iş parçacığında hiçbir şekilde çağrılmaz.</span><span class="sxs-lookup"><span data-stu-id="126f6-106">The `ReleaseAllRuntimeThreads` method will never be called on a runtime thread.</span></span> <span data-ttu-id="126f6-107">Konakta engellenen bir çalışma zamanı iş parçacığı varsa, şimdi onu serbest bırakmalıdır.</span><span class="sxs-lookup"><span data-stu-id="126f6-107">If the host has a runtime thread blocked, it should release it now.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="126f6-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="126f6-108">Requirements</span></span>  
 <span data-ttu-id="126f6-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="126f6-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="126f6-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="126f6-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="126f6-111">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="126f6-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="126f6-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="126f6-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126f6-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="126f6-113">See also</span></span>

- [<span data-ttu-id="126f6-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="126f6-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
