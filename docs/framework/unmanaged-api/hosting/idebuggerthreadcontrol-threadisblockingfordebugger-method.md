---
title: IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi
ms.date: 03/30/2017
api_name:
- IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 47ff178cc9ab798593848e56fc7bba8ac82ae295
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59154238"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="e294f-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="e294f-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="e294f-103">Bu geri gönderme iş parçacığı hakkında konağa bildirir blok içinde hata ayıklama Hizmetleri için.</span><span class="sxs-lookup"><span data-stu-id="e294f-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e294f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="e294f-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="e294f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="e294f-105">Remarks</span></span>  
 <span data-ttu-id="e294f-106">`ThreadIsBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığı üzerinde her zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="e294f-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="e294f-107">`ThreadIsBlockingForDebugger` Yöntemi ana iş parçacığı blokları çalışırken başka bir eylem gerçekleştirmek için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="e294f-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e294f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="e294f-108">Requirements</span></span>  
 <span data-ttu-id="e294f-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e294f-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e294f-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e294f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e294f-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="e294f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="e294f-112">.NET Framework sürümleri:</span><span class="sxs-lookup"><span data-stu-id="e294f-112">NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e294f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="e294f-113">See also</span></span>

- [<span data-ttu-id="e294f-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="e294f-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
