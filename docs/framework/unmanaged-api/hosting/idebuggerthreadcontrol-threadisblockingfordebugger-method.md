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
ms.openlocfilehash: 9766c71c568c9661cf284e9c05eb2dd7634a95aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437436"
---
# <a name="idebuggerthreadcontrolthreadisblockingfordebugger-method"></a><span data-ttu-id="b2a41-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Yöntemi</span><span class="sxs-lookup"><span data-stu-id="b2a41-102">IDebuggerThreadControl::ThreadIsBlockingForDebugger Method</span></span>
<span data-ttu-id="b2a41-103">Bu geri çağırma gönderme iş parçacığı hakkındadır konak bildirir hata ayıklama Hizmetleri blokta için.</span><span class="sxs-lookup"><span data-stu-id="b2a41-103">Notifies the host that the thread that is sending this callback is about to block within the debugging services.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2a41-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="b2a41-104">Syntax</span></span>  
  
```  
HRESULT ThreadIsBlockingForDebugger ( );  
```  
  
## <a name="remarks"></a><span data-ttu-id="b2a41-105">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="b2a41-105">Remarks</span></span>  
 <span data-ttu-id="b2a41-106">`ThreadIsBlockingForDebugger` Yöntemi bir çalışma zamanı iş parçacığı üzerinde her zaman çağrılır.</span><span class="sxs-lookup"><span data-stu-id="b2a41-106">The `ThreadIsBlockingForDebugger` method will always be called on a runtime thread.</span></span>  
  
 <span data-ttu-id="b2a41-107">`ThreadIsBlockingForDebugger` Yöntemi ana iş parçacığı blokları çalışırken başka bir eylem gerçekleştirmek için bir fırsat sunar.</span><span class="sxs-lookup"><span data-stu-id="b2a41-107">The `ThreadIsBlockingForDebugger` method gives the host an opportunity to perform another action while the thread blocks.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2a41-108">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="b2a41-108">Requirements</span></span>  
 <span data-ttu-id="b2a41-109">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2a41-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2a41-110">**Başlık:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b2a41-110">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b2a41-111">**Kitaplığı:** bir kaynak olarak MSCorEE.dll dahil</span><span class="sxs-lookup"><span data-stu-id="b2a41-111">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b2a41-112">**.NET Framework sürümleri:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2a41-112">**NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2a41-113">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="b2a41-113">See Also</span></span>  
 [<span data-ttu-id="b2a41-114">IDebuggerThreadControl Arabirimi</span><span class="sxs-lookup"><span data-stu-id="b2a41-114">IDebuggerThreadControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)
