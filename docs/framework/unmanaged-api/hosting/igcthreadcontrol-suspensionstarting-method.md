---
title: IGCThreadControl::SuspensionStarting Yöntemi
ms.date: 03/30/2017
api_name:
- IGCThreadControl.SuspensionStarting
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SuspensionStarting
helpviewer_keywords:
- IGCThreadControl::SuspensionStarting method [.NET Framework hosting]
- SuspensionStarting method, IGCThreadControl interface [.NET Framework hosting]
ms.assetid: 0af312af-98e9-415e-b182-42e80a1aee51
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7613bc744ad4c2e172fc4f6dd7bf282fb3d9072c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179757"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="c47bb-102">IGCThreadControl::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c47bb-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="c47bb-103">Konak, çalışma zamanının çöp toplama için bir iş parçacığını askıya alma ya da diğer ertelenmesi başlıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="c47bb-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c47bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c47bb-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c47bb-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c47bb-105">Remarks</span></span>  
 <span data-ttu-id="c47bb-106">Herhangi bir iş parçacığı sırasında yeniden değil `SuspensionStarting` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="c47bb-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c47bb-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c47bb-107">Requirements</span></span>  
 <span data-ttu-id="c47bb-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c47bb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c47bb-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c47bb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c47bb-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c47bb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="c47bb-111">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="c47bb-111">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c47bb-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c47bb-112">See also</span></span>

- [<span data-ttu-id="c47bb-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c47bb-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
