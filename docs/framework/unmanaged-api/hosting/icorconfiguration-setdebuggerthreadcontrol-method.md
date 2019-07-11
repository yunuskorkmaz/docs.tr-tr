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
ms.openlocfilehash: ebbc076f52c661a394eff51954fceefe8e439ded
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67779885"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="9f263-102">ICorConfiguration::SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="9f263-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="9f263-103">Ortak dil çalışma zamanı (CLR) iş parçacığı engellenir ve engeli kaldırılmış, hata ayıklama için hata ayıklama Hizmetleri çağıran bir geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="9f263-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f263-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="9f263-104">Syntax</span></span>  
  
```cpp  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f263-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="9f263-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="9f263-106">[in] Bir işaretçi bir [Idebuggerthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) konak engelleme ve hata ayıklama Hizmetleri tarafından iş parçacıklarının engellemesinin kaldırılması hakkında uyaran bir nesne.</span><span class="sxs-lookup"><span data-stu-id="9f263-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9f263-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="9f263-107">Requirements</span></span>  
 <span data-ttu-id="9f263-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9f263-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9f263-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9f263-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9f263-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="9f263-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9f263-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9f263-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f263-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="9f263-112">See also</span></span>

- [<span data-ttu-id="9f263-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="9f263-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
