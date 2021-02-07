---
description: ': IDebuggerThreadControl:: StartBlockingForDebugger Yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 3e19817c4adbefd1dd70be047656b3fea261c389
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709687"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="b64c3-103">IDebuggerThreadControl::StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b64c3-103">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>

<span data-ttu-id="b64c3-104">Tüm iş parçacıklarını engellemeye başlamak için hata ayıklama hizmetlerinin olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="b64c3-104">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b64c3-105">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b64c3-105">Syntax</span></span>  
  
```cpp  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b64c3-106">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b64c3-106">Parameters</span></span>  

 `dwUnused`  
 <span data-ttu-id="b64c3-107">'ndaki Gelecekte kullanılmak üzere ayrılmıştır.</span><span class="sxs-lookup"><span data-stu-id="b64c3-107">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b64c3-108">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b64c3-108">Remarks</span></span>  

 <span data-ttu-id="b64c3-109">`StartBlockingForDebugger`Yöntemi bir çalışma zamanı iş parçacığında çağrılabilir.</span><span class="sxs-lookup"><span data-stu-id="b64c3-109">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b64c3-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b64c3-110">Requirements</span></span>  

 <span data-ttu-id="b64c3-111">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b64c3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b64c3-112">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="b64c3-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b64c3-113">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="b64c3-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b64c3-114">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b64c3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b64c3-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b64c3-115">See also</span></span>

- [<span data-ttu-id="b64c3-116">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b64c3-116">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
