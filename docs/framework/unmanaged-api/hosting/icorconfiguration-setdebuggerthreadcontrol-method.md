---
title: ICorConfiguration::SetDebuggerThreadControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetDebuggerThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetDebuggerThreadControl
helpviewer_keywords:
- SetDebuggerThreadControl method [.NET Framework hosting]
- ICorConfiguration::SetDebuggerThreadControl method [.NET Framework hosting]
ms.assetid: 1ded7639-dacb-4db1-961c-d1ceaec01959
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 449546a0f774a241efd035190d43de103199edbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436812"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="1201e-102">ICorConfiguration::SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="1201e-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="1201e-103">Hata Ayıklama Hizmetleri ortak dil çalışma zamanı (CLR) iş parçacıklarının çağıracak geri çağırma arabirimi bloke ve hata ayıklama için engellemesini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="1201e-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1201e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="1201e-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1201e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="1201e-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="1201e-106">[in] Bir işaretçi bir [Idebuggerthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) konak engelleme ve hata ayıklama Hizmetleri tarafından iş parçacıklarının kaldırma hakkında bilgilendirir nesnesi.</span><span class="sxs-lookup"><span data-stu-id="1201e-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1201e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="1201e-107">Requirements</span></span>  
 <span data-ttu-id="1201e-108">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1201e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1201e-109">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="1201e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1201e-110">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="1201e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1201e-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1201e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1201e-112">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="1201e-112">See Also</span></span>  
 [<span data-ttu-id="1201e-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="1201e-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
