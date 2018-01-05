---
title: "ICorConfiguration::SetDebuggerThreadControl Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetDebuggerThreadControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46bd2b7a40cbcf4f68b8c2f62fea466aa17f2d31
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="973bb-102">ICorConfiguration::SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="973bb-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="973bb-103">Hata Ayıklama Hizmetleri ortak dil çalışma zamanı (CLR) iş parçacıklarının çağıracak geri çağırma arabirimi bloke ve hata ayıklama için engellemesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="973bb-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="973bb-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="973bb-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="973bb-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="973bb-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="973bb-106">[in] Bir işaretçi bir [Idebuggerthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) konak engelleme ve hata ayıklama Hizmetleri tarafından iş parçacıklarının kaldırma hakkında bilgilendirir nesnesi.</span><span class="sxs-lookup"><span data-stu-id="973bb-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="973bb-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="973bb-107">Requirements</span></span>  
 <span data-ttu-id="973bb-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="973bb-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="973bb-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="973bb-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="973bb-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="973bb-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="973bb-111">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="973bb-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="973bb-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="973bb-112">See Also</span></span>  
 [<span data-ttu-id="973bb-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="973bb-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
