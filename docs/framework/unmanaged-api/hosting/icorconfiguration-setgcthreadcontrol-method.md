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
ms.openlocfilehash: b50c87efeb8ad2311a75886da677a9dc901bca1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135843"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a><span data-ttu-id="b783f-102">ICorConfiguration::SetGCThreadControl Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b783f-102">ICorConfiguration::SetGCThreadControl Method</span></span>
<span data-ttu-id="b783f-103">Bir çöp toplama işlemi için normalde engellenecek çalışma zamanı olmayan görevler için iş parçacıklarını zamanlama için geri arama arabirimini ayarlar.</span><span class="sxs-lookup"><span data-stu-id="b783f-103">Sets the callback interface for scheduling threads for non-runtime tasks that would otherwise be blocked for a garbage collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b783f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b783f-104">Syntax</span></span>  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b783f-105">Parametreler</span><span class="sxs-lookup"><span data-stu-id="b783f-105">Parameters</span></span>  
 `pGCThreadControl`  
 <span data-ttu-id="b783f-106">[in] Bir işaretçi bir [Igcthreadcontrol](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) konak çalışma zamanı olmayan görevler için iş parçacıkları askıya alınması hakkında uyaran bir nesne.</span><span class="sxs-lookup"><span data-stu-id="b783f-106">[in] A pointer to an [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) object that notifies the host about the suspension of threads for non-runtime tasks.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b783f-107">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b783f-107">Remarks</span></span>  
 <span data-ttu-id="b783f-108">Konak içinde tercih edebilirsiniz [Igcthreadcontrol::threadısblockingforsuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) geri çağırma kullanılıp bir iş parçacığı yeniden zamanlamak.</span><span class="sxs-lookup"><span data-stu-id="b783f-108">The host may choose within the [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) callback whether to reschedule a thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b783f-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b783f-109">Requirements</span></span>  
 <span data-ttu-id="b783f-110">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b783f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b783f-111">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b783f-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b783f-112">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b783f-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="b783f-113">.NET framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="b783f-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b783f-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="b783f-114">See also</span></span>

- [<span data-ttu-id="b783f-115">ICorConfiguration Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b783f-115">ICorConfiguration Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
