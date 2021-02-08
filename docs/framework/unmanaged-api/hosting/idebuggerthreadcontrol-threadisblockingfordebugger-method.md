---
description: ': IDebuggerThreadControl:: Threadıblockingfordebugger yöntemi hakkında daha fazla bilgi edinin'
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
ms.openlocfilehash: 0fa96b2e36ea6653e1698dd32fa1e73d223afb94
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789521"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="c8fa2-103">IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="c8fa2-103">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>

<span data-ttu-id="c8fa2-104">Konağa, bu geri aramayı gönderen iş parçacığının hata ayıklama Hizmetleri içinde engellemek üzere olduğunu bildirir.</span><span class="sxs-lookup"><span data-stu-id="c8fa2-104">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8fa2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c8fa2-105">Syntax</span></span>  
  
```cpp  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="c8fa2-106">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="c8fa2-106">Remarks</span></span>  

 <span data-ttu-id="c8fa2-107">`ThreadIsBlockingForDebugger`Yöntemi her zaman bir çalışma zamanı iş parçacığında çağrılır.</span><span class="sxs-lookup"><span data-stu-id="c8fa2-107">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="c8fa2-108">`ThreadIsBlockingForDebugger`Yöntemi, iş parçacığı engellediğinde ana bilgisayara başka bir eylem gerçekleştirme fırsatı verir.</span><span class="sxs-lookup"><span data-stu-id="c8fa2-108">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8fa2-109">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="c8fa2-109">Requirements</span></span>  

 <span data-ttu-id="c8fa2-110">**Platformlar:** Bkz. [sistem gereksinimleri](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8fa2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8fa2-111">**Üst bilgi:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="c8fa2-111">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="c8fa2-112">**Kitaplık:** MSCorEE.dll bir kaynak olarak eklendi</span><span class="sxs-lookup"><span data-stu-id="c8fa2-112">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c8fa2-113">**Net Framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8fa2-113">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8fa2-114">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="c8fa2-114">See also</span></span>

- [<span data-ttu-id="c8fa2-115">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="c8fa2-115">IDebuggerThreadControl Interface</span></span>](idebuggerthreadcontrol-interface.md)
