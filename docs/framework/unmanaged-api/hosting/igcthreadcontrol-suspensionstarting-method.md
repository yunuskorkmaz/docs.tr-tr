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
ms.openlocfilehash: 7cb58593a30b855c9fabf55a6ca0a50886dc371f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779488"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="fb14f-102">IGCThreadControl::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="fb14f-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="fb14f-103">Konak, çalışma zamanının çöp toplama için bir iş parçacığını askıya alma ya da diğer ertelenmesi başlıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="fb14f-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fb14f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="fb14f-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="fb14f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="fb14f-105">Remarks</span></span>  
 <span data-ttu-id="fb14f-106">Herhangi bir iş parçacığı sırasında yeniden değil `SuspensionStarting` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="fb14f-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fb14f-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="fb14f-107">Requirements</span></span>  
 <span data-ttu-id="fb14f-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fb14f-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fb14f-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="fb14f-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fb14f-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="fb14f-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fb14f-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fb14f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb14f-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="fb14f-112">See also</span></span>

- [<span data-ttu-id="fb14f-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="fb14f-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
