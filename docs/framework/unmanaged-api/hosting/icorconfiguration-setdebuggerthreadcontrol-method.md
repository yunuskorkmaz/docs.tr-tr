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
ms.openlocfilehash: 6fc141cbebe08f8d0974788409d5aef0f68d2878
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763262"
---
# <a name="icorconfigurationsetdebuggerthreadcontrol-method"></a><span data-ttu-id="4dd8e-102">ICorConfiguration::SetDebuggerThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="4dd8e-102">ICorConfiguration::SetDebuggerThreadControl Method</span></span>
<span data-ttu-id="4dd8e-103">Ortak dil çalışma zamanı (CLR) iş parçacığı engellenir ve engeli kaldırılmış, hata ayıklama için hata ayıklama Hizmetleri çağıran bir geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="4dd8e-103">Sets the callback interface that the debugging services will call as common language runtime (CLR) threads are blocked and unblocked for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd8e-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="4dd8e-104">Syntax</span></span>  
  
```  
HRESULT SetDebuggerThreadControl (  
    [in] IDebuggerThreadControl* pDebuggerThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4dd8e-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="4dd8e-105">Parameters</span></span>  
 `pDebuggerThreadControl`  
 <span data-ttu-id="4dd8e-106">[in] Bir işaretçi bir [Idebuggerthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) konak engelleme ve hata ayıklama Hizmetleri tarafından iş parçacıklarının engellemesinin kaldırılması hakkında uyaran bir nesne.</span><span class="sxs-lookup"><span data-stu-id="4dd8e-106">[in] A pointer to an [IDebuggerThreadControl](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md) object that notifies the host about the blocking and unblocking of threads by the debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dd8e-107">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="4dd8e-107">Requirements</span></span>  
 <span data-ttu-id="4dd8e-108">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dd8e-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dd8e-109">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="4dd8e-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4dd8e-110">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="4dd8e-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4dd8e-111">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dd8e-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dd8e-112">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="4dd8e-112">See also</span></span>

- [<span data-ttu-id="4dd8e-113">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="4dd8e-113">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
