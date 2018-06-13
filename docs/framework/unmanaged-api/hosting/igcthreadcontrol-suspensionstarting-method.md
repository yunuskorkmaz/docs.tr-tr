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
ms.openlocfilehash: 95cbda3729c02b95557f9f700f1ea7c68aa450a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33438021"
---
# <a name="igcthreadcontrolsuspensionstarting-method"></a><span data-ttu-id="c8735-102">IGCThreadControl::SuspensionStarting Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8735-102">IGCThreadControl::SuspensionStarting Method</span></span>
<span data-ttu-id="c8735-103">Ana bilgisayar, çalışma zamanı modülü çöp toplama için bir iş parçacığı askıya alınması veya diğer askıya başlıyor bildirir.</span><span class="sxs-lookup"><span data-stu-id="c8735-103">Notifies the host that the runtime is beginning a thread suspension for a garbage collection or other suspension.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8735-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="c8735-104">Syntax</span></span>  
  
```  
HRESULT SuspensionStarting ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c8735-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8735-105">Remarks</span></span>  
 <span data-ttu-id="c8735-106">Tüm iş parçacıklarının sırasında yeniden zamanla değil `SuspensionStarting` geri çağırma.</span><span class="sxs-lookup"><span data-stu-id="c8735-106">Do not reschedule any threads during the `SuspensionStarting` callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8735-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8735-107">Requirements</span></span>  
 <span data-ttu-id="c8735-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8735-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8735-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="c8735-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8735-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="c8735-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8735-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8735-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8735-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="c8735-112">See Also</span></span>  
 [<span data-ttu-id="c8735-113">IGCThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8735-113">IGCThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)
