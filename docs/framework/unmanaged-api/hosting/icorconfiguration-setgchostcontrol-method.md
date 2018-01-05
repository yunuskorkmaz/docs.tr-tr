---
title: "ICorConfiguration::SetGCHostControl Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetGCHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98f36fea9705d212b01a0220cca321192b8193d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetgchostcontrol-method"></a><span data-ttu-id="d549e-102">ICorConfiguration::SetGCHostControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="d549e-102">ICorConfiguration::SetGCHostControl Method</span></span>
<span data-ttu-id="d549e-103">Geri çağırma arabirimi sanal bellek sınırları değiştirmek için ana istemek için atık toplayıcısı tarafından kullanılacak ayarlar.</span><span class="sxs-lookup"><span data-stu-id="d549e-103">Sets the callback interface to be used by the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d549e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="d549e-104">Syntax</span></span>  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d549e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="d549e-105">Parameters</span></span>  
 `pGCHostControl`  
 <span data-ttu-id="d549e-106">[in] Bir işaretçi bir [Igchostcontrol](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) sanal bellek sınırları değiştirmek için ana istemek atık toplayıcı veren nesnesi.</span><span class="sxs-lookup"><span data-stu-id="d549e-106">[in] A pointer to an [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) object that allows the garbage collector to request the host to change the limits of virtual memory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d549e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="d549e-107">Requirements</span></span>  
 <span data-ttu-id="d549e-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d549e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d549e-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="d549e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d549e-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="d549e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d549e-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d549e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d549e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d549e-112">See Also</span></span>  
 [<span data-ttu-id="d549e-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="d549e-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
