---
title: "IGCThreadControl::SuspensionEnding Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IGCThreadControl.SuspensionEnding
api_location: mscoree.dll
api_type: COM
f1_keywords: SuspensionEnding
helpviewer_keywords:
- IGCThreadControl::SuspensionEnding method [.NET Framework hosting]
- SuspensionEnding method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 70814265-c734-4ddc-9502-fe8b28d2b414
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e4460d2b0eaf10d20ddd0c3641279a8ffc05c245
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2017
---
# <a name="igcthreadcontrolsuspensionending-method"></a><span data-ttu-id="ae545-102">IGCThreadControl::SuspensionEnding Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ae545-102">IGCThreadControl::SuspensionEnding Method</span></span>
<span data-ttu-id="ae545-103">Konak bir atık toplama veya diğer askıya sonra çalışma zamanı iş parçacıklarını sürdürme olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="ae545-103">Notifies the host that the runtime is resuming threads after a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae545-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ae545-104">Syntax</span></span>  
  
```  
HRESULT SuspensionEnding (  
    [in] DWORD Generation  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ae545-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ae545-105">Parameters</span></span>  
 `Generation`  
 <span data-ttu-id="ae545-106">[in] Çöp toplama gerçekleştirilmiş olan oluşturma.</span><span class="sxs-lookup"><span data-stu-id="ae545-106">[in] The generation on which a garbage collection has been performed.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ae545-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ae545-107">Remarks</span></span>  
 <span data-ttu-id="ae545-108">Tüm iş parçacıklarının sırasında yeniden zamanla değil `SuspensionEnding` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="ae545-108">Do not reschedule any threads during the `SuspensionEnding` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae545-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ae545-109">Requirements</span></span>  
 <span data-ttu-id="ae545-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ae545-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae545-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ae545-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ae545-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ae545-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ae545-113">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae545-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae545-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ae545-114">See Also</span></span>  
 [<span data-ttu-id="ae545-115">Igcthreadcontrol arabirimi</span><span class="sxs-lookup"><span data-stu-id="ae545-115">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
