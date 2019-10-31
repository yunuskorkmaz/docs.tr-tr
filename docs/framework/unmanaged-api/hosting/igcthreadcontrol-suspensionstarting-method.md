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
ms.openlocfilehash: 1e1d63ab28276f69e5b3a762520db8f8300d05bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134755"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="cec31-102">IGCThreadControl::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="cec31-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="cec31-103">Bir atık toplama veya başka bir askıya alma için bir iş parçacığının askıya alınma zamanı olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="cec31-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cec31-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="cec31-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="cec31-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="cec31-105">Remarks</span></span>  
 <span data-ttu-id="cec31-106">`SuspensionStarting` geri çağırma sırasında herhangi bir iş parçacığını yeniden zamanlamayın.</span><span class="sxs-lookup"><span data-stu-id="cec31-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cec31-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="cec31-107">Requirements</span></span>  
 <span data-ttu-id="cec31-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cec31-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cec31-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="cec31-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cec31-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="cec31-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cec31-111">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cec31-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec31-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="cec31-112">See also</span></span>

- [<span data-ttu-id="cec31-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="cec31-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
