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
ms.openlocfilehash: 72f7bee79e74c69acff90861ceada8a91afe2157
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134913"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="0e360-102">IDebuggerThreadControl::StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0e360-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="0e360-103">Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="0e360-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e360-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0e360-104">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e360-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0e360-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="0e360-106">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="0e360-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0e360-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0e360-107">Remarks</span></span>  
 <span data-ttu-id="0e360-108">`StartBlockingForDebugger` yöntemi bir çalışma zamanı iş parçacığında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="0e360-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0e360-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0e360-109">Requirements</span></span>  
 <span data-ttu-id="0e360-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e360-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e360-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e360-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e360-112">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="0e360-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e360-113">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e360-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e360-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="0e360-114">See also</span></span>

- [<span data-ttu-id="0e360-115">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="0e360-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
