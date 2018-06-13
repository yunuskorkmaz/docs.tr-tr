---
title: ICorConfiguration::SetGCThreadControl Yöntemi
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9da3c0ee081b81411d13dfcf9c8557c6bd4d3448
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437313"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="ce93a-102">ICorConfiguration::SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="ce93a-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="ce93a-103">Çöp toplama için engellenmesi çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri çağırma arabirimi ayarlar.</span><span class="sxs-lookup"><span data-stu-id="ce93a-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce93a-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="ce93a-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ce93a-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="ce93a-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="ce93a-106">[in] Bir işaretçi bir [Igcthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) konak çalışma zamanı olmayan görevler için iş parçacıklarını askıya alma hakkında bilgilendirir nesnesi.</span><span class="sxs-lookup"><span data-stu-id="ce93a-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce93a-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="ce93a-107">Remarks</span></span>  
 <span data-ttu-id="ce93a-108">Konak içinde tercih edebilirsiniz [Igcthreadcontrol::threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) geri çağırma kullanılıp bir iş parçacığı yeniden zamanlamak.</span><span class="sxs-lookup"><span data-stu-id="ce93a-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce93a-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="ce93a-109">Requirements</span></span>  
 <span data-ttu-id="ce93a-110">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce93a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce93a-111">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ce93a-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ce93a-112">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="ce93a-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ce93a-113">**.NET framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce93a-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce93a-114">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="ce93a-114">See Also</span></span>  
 [<span data-ttu-id="ce93a-115">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="ce93a-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
