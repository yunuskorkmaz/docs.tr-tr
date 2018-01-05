---
title: "IDebuggerThreadControl::StartBlockingForDebugger Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.StartBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: StartBlockingForDebugger
helpviewer_keywords:
- IDebuggerThreadControl::StartBlockingForDebugger method [.NET Framework hosting]
- StartBlockingForDebugger method [.NET Framework hosting]
ms.assetid: 5c8f11b4-35d3-4c39-9bbd-58b896ba5ba6
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 99c0bc78705fa07883d92bf0cc1d90300c5ac549
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="6e617-102">IDebuggerThreadControl::StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="6e617-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="6e617-103">Ana bilgisayar hata ayıklama hizmetleri hakkında tüm iş parçacıklarının engelleme başlangıç olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="6e617-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e617-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="6e617-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e617-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="6e617-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="6e617-106">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="6e617-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e617-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="6e617-107">Remarks</span></span>  
 <span data-ttu-id="6e617-108">`StartBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığında adlı.</span><span class="sxs-lookup"><span data-stu-id="6e617-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e617-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="6e617-109">Requirements</span></span>  
 <span data-ttu-id="6e617-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6e617-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e617-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6e617-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e617-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="6e617-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e617-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e617-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e617-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="6e617-114">See Also</span></span>  
 [<span data-ttu-id="6e617-115">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="6e617-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
