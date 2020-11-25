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
ms.openlocfilehash: 8c2741d7db60781fef12293f3be0b515a55b7885
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705520"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="f154f-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="f154f-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>

<span data-ttu-id="f154f-103">Konağa, bu geri aramayı gönderen iş parçacığının hata ayıklama Hizmetleri içinde engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="f154f-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f154f-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f154f-104">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="f154f-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="f154f-105">Remarks</span></span>  

 <span data-ttu-id="f154f-106">`ThreadIsBlockingForDebugger`Yöntemi her zaman bir çalışma zamanı iş parçacığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="f154f-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="f154f-107">`ThreadIsBlockingForDebugger`Yöntemi, iş parçacığı engellediğinde ana bilgisayara başka bir eylem gerçekleştirme fırsatı verir.</span><span class="sxs-lookup"><span data-stu-id="f154f-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f154f-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="f154f-108">Requirements</span></span>  

 <span data-ttu-id="f154f-109">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f154f-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f154f-110">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f154f-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f154f-111">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="f154f-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f154f-112">**Net Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f154f-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f154f-113">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="f154f-113">See also</span></span>

- [<span data-ttu-id="f154f-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="f154f-114">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
