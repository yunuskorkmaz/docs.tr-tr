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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61992764"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="3cbb7-102">IGCThreadControl::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="3cbb7-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="3cbb7-103">Konak, çalışma zamanının çöp toplama için bir iş parçacığını askıya alma ya da diğer ertelenmesi başlıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="3cbb7-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cbb7-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="3cbb7-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="3cbb7-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="3cbb7-105">Remarks</span></span>  
 <span data-ttu-id="3cbb7-106">Herhangi bir iş parçacığı sırasında yeniden değil `SuspensionStarting` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="3cbb7-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cbb7-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="3cbb7-107">Requirements</span></span>  
 <span data-ttu-id="3cbb7-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3cbb7-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cbb7-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="3cbb7-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="3cbb7-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="3cbb7-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="3cbb7-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cbb7-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cbb7-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="3cbb7-112">See also</span></span>

- [<span data-ttu-id="3cbb7-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="3cbb7-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
