---
title: "IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDebuggerThreadControl.ThreadIsBlockingForDebugger
api_location: mscoree.dll
api_type: COM
f1_keywords: ThreadIsBlockingForDebugger
helpviewer_keywords:
- ThreadIsBlockingForDebugger method [.NET Framework hosting]
- IDebuggerThreadControl::ThreadIsBlockingForDebugger method [.NET Framework hosting]
ms.assetid: d4d7cb2d-69da-48b3-879a-1a8a68c9bfa8
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 59a4c13e84414dcd10b217134334777a745431c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="2d8ab-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="2d8ab-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="2d8ab-103">Bu geri çağırma gönderme iş parçacığı hakkındadır konak bildirir hata ayıklama Hizmetleri blokta için.</span><span class="sxs-lookup"><span data-stu-id="2d8ab-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d8ab-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="2d8ab-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="2d8ab-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="2d8ab-105">Remarks</span></span>  
 <span data-ttu-id="2d8ab-106">`ThreadIsBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığı üzerinde her zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="2d8ab-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="2d8ab-107">`ThreadIsBlockingForDebugger` Yöntemi ana iş parçacığı blokları çalışırken başka bir eylem gerçekleştirmek için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="2d8ab-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d8ab-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="2d8ab-108">Requirements</span></span>  
 <span data-ttu-id="2d8ab-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d8ab-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d8ab-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="2d8ab-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2d8ab-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="2d8ab-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2d8ab-112">**NET Framework sürümlerini:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d8ab-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d8ab-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="2d8ab-113">See Also</span></span>  
 [<span data-ttu-id="2d8ab-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="2d8ab-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
