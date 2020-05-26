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
ms.openlocfilehash: 2acabe66e3b6b5652df20e31a9d2294c2396b54b
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805095"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="7e9d9-102">IGCThreadControl::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="7e9d9-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="7e9d9-103">Bir atık toplama veya başka bir askıya alma için bir iş parçacığının askıya alınma zamanı olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="7e9d9-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e9d9-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="7e9d9-104">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="7e9d9-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="7e9d9-105">Remarks</span></span>  
 <span data-ttu-id="7e9d9-106">Geri çağırma sırasında herhangi bir iş parçacığını yeniden zamanlamayın `SuspensionStarting` .</span><span class="sxs-lookup"><span data-stu-id="7e9d9-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e9d9-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7e9d9-107">Requirements</span></span>  
 <span data-ttu-id="7e9d9-108">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e9d9-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e9d9-109">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7e9d9-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7e9d9-110">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="7e9d9-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7e9d9-111">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e9d9-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e9d9-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="7e9d9-112">See also</span></span>

- [<span data-ttu-id="7e9d9-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="7e9d9-113">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
