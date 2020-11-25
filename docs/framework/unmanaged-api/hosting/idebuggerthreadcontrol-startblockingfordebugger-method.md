---
title: IDebuggerThreadControl::StartBlockingForDebugger Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.StartBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type:
- apiref
ms.openlocfilehash: 1e0cb52a6b9f03209256e5398415b4ec632fb5e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705515"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="3547b-102">IDebuggerThreadControl::StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3547b-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>

<span data-ttu-id="3547b-103">Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="3547b-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3547b-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="3547b-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3547b-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="3547b-105">Parameters</span></span>  

 `dwUnused`  
 <span data-ttu-id="3547b-106">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="3547b-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3547b-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3547b-107">Remarks</span></span>  

 <span data-ttu-id="3547b-108">`StartBlockingForDebugger`Yöntemi bir çalışma zamanı iş parçacığında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="3547b-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3547b-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3547b-109">Requirements</span></span>  

 <span data-ttu-id="3547b-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3547b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3547b-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="3547b-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3547b-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="3547b-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3547b-113">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3547b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3547b-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3547b-114">See also</span></span>

- [<span data-ttu-id="3547b-115">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3547b-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
