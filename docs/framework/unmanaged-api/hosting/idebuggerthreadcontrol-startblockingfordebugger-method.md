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
ms.openlocfilehash: 0f7d49766c68c24441bf59d2d83958276def0143
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="idebuggerthreadcontrolstartblockingfordebugger-method"></a><span data-ttu-id="0fdda-102">IDebuggerThreadControl::StartBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="0fdda-102">IDebuggerThreadControl::StartBlockingForDebugger Method</span></span>
<span data-ttu-id="0fdda-103">Ana bilgisayar hata ayıklama hizmetleri hakkında tüm iş parçacıklarının engelleme başlangıç olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="0fdda-103">Notifies the host that the debugging services are about to start blocking all threads.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fdda-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="0fdda-104">Syntax</span></span>  
  
```  
HRESULT StartBlockingForDebugger (  
    [in] DWORD dwUnused  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0fdda-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="0fdda-105">Parameters</span></span>  
 `dwUnused`  
 <span data-ttu-id="0fdda-106">[in] Gelecekte kullanılmak üzere ayrılmış.</span><span class="sxs-lookup"><span data-stu-id="0fdda-106">[in] Reserved for future use.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fdda-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="0fdda-107">Remarks</span></span>  
 <span data-ttu-id="0fdda-108">`StartBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığında adlı.</span><span class="sxs-lookup"><span data-stu-id="0fdda-108">The `StartBlockingForDebugger` method could be called on a runtime thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fdda-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="0fdda-109">Requirements</span></span>  
 <span data-ttu-id="0fdda-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fdda-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fdda-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="0fdda-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0fdda-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="0fdda-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0fdda-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fdda-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fdda-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="0fdda-114">See Also</span></span>  
 [<span data-ttu-id="0fdda-115">Idebuggerthreadcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="0fdda-115">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
