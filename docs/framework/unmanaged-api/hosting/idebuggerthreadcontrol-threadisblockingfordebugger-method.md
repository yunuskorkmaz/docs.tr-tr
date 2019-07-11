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
ms.openlocfilehash: 9324e1596913fdafb13239dbefd631cbe3c6ffe4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780484"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="39e27-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="39e27-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="39e27-103">Bu geri gönderme iş parçacığı hakkında konağa bildirir blok içinde hata ayıklama Hizmetleri için.</span><span class="sxs-lookup"><span data-stu-id="39e27-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e27-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="39e27-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="39e27-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="39e27-105">Remarks</span></span>  
 <span data-ttu-id="39e27-106">`ThreadIsBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığı üzerinde her zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="39e27-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="39e27-107">`ThreadIsBlockingForDebugger` Yöntemi ana iş parçacığı blokları çalışırken başka bir eylem gerçekleştirmek için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="39e27-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="39e27-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="39e27-108">Requirements</span></span>  
 <span data-ttu-id="39e27-109">**Platformlar:** Bkz: [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="39e27-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="39e27-110">**Üst bilgi:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="39e27-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="39e27-111">**Kitaplığı:** Bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="39e27-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="39e27-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="39e27-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39e27-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="39e27-113">See also</span></span>

- [<span data-ttu-id="39e27-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="39e27-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
