---
description: 'Daha fazla bilgi edinin: IGCThreadControl:: SuspensionStarting yöntemi'
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
ms.openlocfilehash: b9d068e6995a73e9a9a31d5d5debf008f9748630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709304"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="996f2-103">IGCThreadControl::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="996f2-103">IGCThreadControl::SuspensionStarting Method</span></span>

<span data-ttu-id="996f2-104">Bir atık toplama veya başka bir askıya alma için bir iş parçacığının askıya alınma zamanı olduğunu konağa bildirir.</span><span class="sxs-lookup"><span data-stu-id="996f2-104">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="996f2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="996f2-105">Syntax</span></span>  
  
```cpp  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="996f2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="996f2-106">Remarks</span></span>  

 <span data-ttu-id="996f2-107">Geri çağırma sırasında herhangi bir iş parçacığını yeniden zamanlamayın `SuspensionStarting` .</span><span class="sxs-lookup"><span data-stu-id="996f2-107">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="996f2-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="996f2-108">Requirements</span></span>  

 <span data-ttu-id="996f2-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="996f2-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="996f2-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="996f2-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="996f2-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="996f2-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="996f2-112">**.NET Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="996f2-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="996f2-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="996f2-113">See also</span></span>

- [<span data-ttu-id="996f2-114">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="996f2-114">IGCThreadControl Interface</span></span>](igcthreadcontrol-interface.md)
