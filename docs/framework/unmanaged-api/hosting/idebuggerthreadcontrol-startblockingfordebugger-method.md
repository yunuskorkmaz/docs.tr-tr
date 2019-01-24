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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 746b61a303869ff03d41cd6005ca0f5635ac0fd5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521731"
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="4e101-102">IDebuggerThreadControl::StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4e101-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="4e101-103">Konak, hata ayıklama Hizmetleri tüm iş parçacıklarının engellemesini başlamak üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="4e101-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e101-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4e101-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4e101-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4e101-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="4e101-106">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="4e101-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e101-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="4e101-107">Remarks</span></span>  
 <span data-ttu-id="4e101-108">`StartBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığında çağrıldı.</span><span class="sxs-lookup"><span data-stu-id="4e101-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e101-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4e101-109">Requirements</span></span>  
 <span data-ttu-id="4e101-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4e101-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e101-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4e101-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4e101-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4e101-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4e101-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e101-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e101-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4e101-114">See also</span></span>
- [<span data-ttu-id="4e101-115">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4e101-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
