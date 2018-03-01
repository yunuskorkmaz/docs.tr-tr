---
title: "CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CLR_DEBUGGING_PROCESS_FLAGS
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_PROCESS_FLAG
helpviewer_keywords:
- CLR_DEBUGGING_PROCESS_FLAGS enumeration [.NET Framework debugging]
ms.assetid: 85b85fde-1f87-490b-ba8d-d604670959c3
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4c6d66f9a11f28ca572e0f1eddc74f3a5197a19d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="clrdebuggingprocessflags-enumeration"></a><span data-ttu-id="33e8f-102">CLR_DEBUGGING_PROCESS_FLAGS Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="33e8f-102">CLR_DEBUGGING_PROCESS_FLAGS Enumeration</span></span>
<span data-ttu-id="33e8f-103">Tarafından kullanılan değerleri sağlayan [Iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) yöntemi.</span><span class="sxs-lookup"><span data-stu-id="33e8f-103">Provides values that are used by the [ICLRDebugging::OpenVirtualProcess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33e8f-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="33e8f-104">Syntax</span></span>  
  
```  
typedef enum CLR_DEBUGGING_PROCESS_FLAGS  
{  
   CLR_DEBUGGING_MANAGED_EVENT_PENDING = 1,  
   CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH = 2  
}  CLR_DEBUGGING_PROCESS_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="33e8f-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="33e8f-105">Members</span></span>  
  
|<span data-ttu-id="33e8f-106">Üye</span><span class="sxs-lookup"><span data-stu-id="33e8f-106">Member</span></span>|<span data-ttu-id="33e8f-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="33e8f-107">Description</span></span>|  
|------------|-----------------|  
|`CLR_DEBUGGING_MANAGED_EVENT_PENDING`|<span data-ttu-id="33e8f-108">Bu çalışma zamanı göndermek için bir catch yukarı yönetilen hata ayıklayıcı olay vardır.</span><span class="sxs-lookup"><span data-stu-id="33e8f-108">This runtime has a non-catch-up managed debugger event to send.</span></span> <span data-ttu-id="33e8f-109">Yakalama ve catch yukarı olayları arasında ayrım için Açıklamalar bölümüne bakın.</span><span class="sxs-lookup"><span data-stu-id="33e8f-109">See the Remarks section for the distinction between catch-up and non-catch-up events.</span></span>|  
|`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH`|<span data-ttu-id="33e8f-110">Beklemede yönetilen olay bir <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> isteği.</span><span class="sxs-lookup"><span data-stu-id="33e8f-110">The managed event that is pending is a <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33e8f-111">Açıklamalar</span><span class="sxs-lookup"><span data-stu-id="33e8f-111">Remarks</span></span>  
 <span data-ttu-id="33e8f-112">İşlem, uygulama etki alanı, derleme, modül ve bir işlemin eklenmiş sonra hata ayıklayıcı kadar geçerli durumuna getirin iş parçacığı oluşturma bildirimleri nım olayları içerir.</span><span class="sxs-lookup"><span data-stu-id="33e8f-112">Catch-up events include process, application domain, assembly, module, and thread creation notifications that bring the debugger up to the current state after it has attached to a process.</span></span> <span data-ttu-id="33e8f-113">Tarafından belirtilen olmayan catch yukarı olayları `CLR_DEBUGGING_MANAGED_EVENT_PENDING` bayrak, hata ayıklama Yardımcısı (MDA) bildirimleri yönetilen ve, tüm diğer hata ayıklayıcı gibi olaylar özel durumları içerir.</span><span class="sxs-lookup"><span data-stu-id="33e8f-113">Non-catch-up events, which are indicated by the `CLR_DEBUGGING_MANAGED_EVENT_PENDING` flag, include all other debugger events, such as exceptions and managed debugging assistant (MDA) notifications.</span></span>  
  
 <span data-ttu-id="33e8f-114">`CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` Bayrağı bir sonlandırma özel durumuyla ve isteği iptal edilebilir yönetilen bir hata ayıklayıcısını arasında ayırt etmek çalışma zamanı sağlar.</span><span class="sxs-lookup"><span data-stu-id="33e8f-114">The `CLR_DEBUGGING_MANAGED_EVENT_DEBUGGER_LAUNCH` flag enables the runtime to differentiate between a terminating exception and a request to attach a managed debugger that can be canceled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33e8f-115">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="33e8f-115">Requirements</span></span>  
 <span data-ttu-id="33e8f-116">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33e8f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33e8f-117">**Başlık:** Metahost.idl, Metahost.h</span><span class="sxs-lookup"><span data-stu-id="33e8f-117">**Header:** Metahost.idl, Metahost.h</span></span>  
  
 <span data-ttu-id="33e8f-118">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33e8f-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33e8f-119">**.NET framework sürümleri:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33e8f-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e8f-120">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="33e8f-120">See Also</span></span>  
 [<span data-ttu-id="33e8f-121">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="33e8f-121">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="33e8f-122">Hata Ayıklama</span><span class="sxs-lookup"><span data-stu-id="33e8f-122">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
