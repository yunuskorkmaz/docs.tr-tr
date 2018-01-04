---
title: "CorDebugExceptionUnwindCallbackType Numaralandırması"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionUnwindCallbackType
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionUnwindCallbackType
helpviewer_keywords: CorDebugExceptionUnwindCallbackType enumeration [.NET Framework debugging]
ms.assetid: 783dce92-8a98-43db-8f78-888d943dd5b2
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c5ee074e55d0d407f89c778c579aa5c4ce03a10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugexceptionunwindcallbacktype-enumeration"></a><span data-ttu-id="7c2b2-102">CorDebugExceptionUnwindCallbackType Numaralandırması</span><span class="sxs-lookup"><span data-stu-id="7c2b2-102">CorDebugExceptionUnwindCallbackType Enumeration</span></span>
<span data-ttu-id="7c2b2-103">Geri çağırma göre geriye doğru izleme aşamasında işaret olay gösterir.</span><span class="sxs-lookup"><span data-stu-id="7c2b2-103">Indicates the event that is being signaled by the callback during the unwind phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c2b2-104">Sözdizimi</span><span class="sxs-lookup"><span data-stu-id="7c2b2-104">Syntax</span></span>  
  
```  
typedef enum CorDebugExceptionUnwindCallbackType {  
    DEBUG_EXCEPTION_UNWIND_BEGIN = 1,  
    DEBUG_EXCEPTION_INTERCEPTED  = 2  
} CorDebugExceptionUnwindCallbackType;  
```  
  
## <a name="members"></a><span data-ttu-id="7c2b2-105">Üyeler</span><span class="sxs-lookup"><span data-stu-id="7c2b2-105">Members</span></span>  
  
|<span data-ttu-id="7c2b2-106">Üye</span><span class="sxs-lookup"><span data-stu-id="7c2b2-106">Member</span></span>|<span data-ttu-id="7c2b2-107">Açıklama</span><span class="sxs-lookup"><span data-stu-id="7c2b2-107">Description</span></span>|  
|------------|-----------------|  
|`DEBUG_EXCEPTION_UNWIND_BEGIN`|<span data-ttu-id="7c2b2-108">Bırakma işlemi başlangıcı.</span><span class="sxs-lookup"><span data-stu-id="7c2b2-108">The beginning of the unwind process.</span></span>|  
|`DEBUG_EXCEPTION_INTERCEPTED`|<span data-ttu-id="7c2b2-109">Özel durum ele.</span><span class="sxs-lookup"><span data-stu-id="7c2b2-109">The exception was intercepted.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7c2b2-110">Gereksinimler</span><span class="sxs-lookup"><span data-stu-id="7c2b2-110">Requirements</span></span>  
 <span data-ttu-id="7c2b2-111">**Platformlar:** bkz [sistem gereksinimleri](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c2b2-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c2b2-112">**Başlık:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c2b2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c2b2-113">**Kitaplığı:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c2b2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c2b2-114">**.NET framework sürümleri:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c2b2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2b2-115">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="7c2b2-115">See Also</span></span>  
 [<span data-ttu-id="7c2b2-116">Hata Ayıklama Sabit Listeleri</span><span class="sxs-lookup"><span data-stu-id="7c2b2-116">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
