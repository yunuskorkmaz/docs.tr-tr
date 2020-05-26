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
ms.openlocfilehash: f7cdc3fe9d52db56d0280bc602d3a9f2f54e8246
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805260"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="5ba93-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="5ba93-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="5ba93-103">Konağa, bu geri aramayı gönderen iş parçacığının hata ayıklama Hizmetleri içinde engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="5ba93-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ba93-104">Söz dizimi</span><span class="sxs-lookup"><span data-stu-id="5ba93-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="5ba93-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="5ba93-105">Remarks</span></span>  
 <span data-ttu-id="5ba93-106">`ThreadIsBlockingForDebugger`Yöntemi her zaman bir çalışma zamanı iş parçacığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="5ba93-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="5ba93-107">`ThreadIsBlockingForDebugger`Yöntemi, iş parçacığı engellediğinde ana bilgisayara başka bir eylem gerçekleştirme fırsatı verir.</span><span class="sxs-lookup"><span data-stu-id="5ba93-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5ba93-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="5ba93-108">Requirements</span></span>  
 <span data-ttu-id="5ba93-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5ba93-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5ba93-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="5ba93-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5ba93-111">**Kitaplık:** MSCorEE. dll dosyasına bir kaynak olarak dahildir</span><span class="sxs-lookup"><span data-stu-id="5ba93-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5ba93-112">**Net Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5ba93-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5ba93-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="5ba93-113">See also</span></span>

- [<span data-ttu-id="5ba93-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="5ba93-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
